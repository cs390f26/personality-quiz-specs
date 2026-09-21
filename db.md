# MySQL data model

Quiz data for this system is stored in **MySQL** using four related tables.

## Access patterns

- Get all quiz questions and their answer choices
- Get a question by id
- Get the personality type associated with an answer
- Calculate a user's personality result from selected answers
- Record a completed quiz result
- Get cumulative quiz result statistics

## Tables

### `questions`

Stores each question used in the fixed personality quiz.

| Column | Type | Notes |
|--------|------|-------|
| `question_ID` | INT | Primary key; unique identifier for the question |
| `question_text` | VARCHAR() | Text displayed for the question |

### `personality_types`

Stores the personality categories that an answer can contribute toward and that can be assigned as a final result.

| Column | Type | Notes |
|--------|------|-------|
| `personality_type_ID` | INT | Primary key; unique identifier for the personality type |
| `personality_type` | VARCHAR() | Name of the personality type |
| `description` | VARCHAR() | Description of the personality type |

### `answers`

Stores the possible answers for each question. Each answer is associated with one personality type.

| Column | Type | Notes |
|--------|------|-------|
| `answer_ID` | INT | Primary key; unique identifier for the answer |
| `question_ID` | INT | Foreign key referencing `questions.question_ID` |
| `answer_text` | VARCHAR() | Text displayed for the answer choice |
| `personality_type_ID` | INT | Foreign key referencing `personality_types.personality_type_ID` |

Each question can have multiple answers. Selecting an answer contributes toward the personality type referenced by `personality_type_ID`.

### `quiz_results`

Stores the final personality result for each completed quiz attempt.

| Column | Type | Notes |
|--------|------|-------|
| `results_ID` | INT | Primary key; unique identifier for the completed quiz result |
| `personality_type_ID` | INT | Foreign key referencing `personality_types.personality_type_ID` |
| `completed_date` | DATE | Date the quiz was completed (`YYYY-MM-DD`) |
| `person_ID` | INT | Identifier used to associate the result with the person or quiz attempt |

## Relationships

- One row in `questions` can have many rows in `answers`.
- One row in `personality_types` can be associated with many rows in `answers`.
- One row in `personality_types` can be associated with many rows in `quiz_results`.
- `person_ID` is stored in `quiz_results`, but no separate person table is defined in this database model.

## Example data

### `questions`

| question_ID | question_text |
|-------------|---------------|
| 1 | Which activity sounds most appealing? |
| 2 | How do you usually approach a new problem? |

### `personality_types`

| personality_type_ID | personality_type | description |
|---------------------|------------------|-------------|
| 1 | Orange | Example personality description |
| 2 | Gold | Example personality description |
| 3 | Green | Example personality description |
| 4 | Blue | Example personality description |

### `answers`

| answer_ID | question_ID | answer_text | personality_type_ID |
|-----------|-------------|-------------|---------------------|
| 1 | 1 | Try something spontaneous | 1 |
| 2 | 1 | Follow a clear plan | 2 |
| 3 | 1 | Learn something challenging | 3 |
| 4 | 1 | Spend time helping someone | 4 |

### `quiz_results`

| results_ID | personality_type_ID | completed_date | person_ID |
|------------|---------------------|----------------|-----------|
| 1 | 3 | 2026-09-18 | 1001 |
| 2 | 2 | 2026-09-18 | 1002 |

## Result calculation

When a user selects an answer, the application uses that answer's `personality_type_ID` to add one point to the corresponding personality type.

After all questions have been answered, the application totals the points for each personality type. The personality type with the highest total becomes the user's final result. A row is then added to `quiz_results` containing the resulting `personality_type_ID`, the completion date, and the user's `person_ID`.

Cumulative statistics can be calculated by counting the number of rows in `quiz_results` for each `personality_type_ID`.
