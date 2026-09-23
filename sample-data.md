# Sample data

Shared fixture for UI mockups, database testing, and automated tests.

This sample data follows the MySQL database model defined for the personality quiz. It includes representative questions, four answer choices per question, the four True Colors personality types, and several completed quiz results.

The quiz contains 10 questions. The questions below are sample records used for development and testing rather than the complete final quiz.

**Machine-readable copy:** [`sample-data.sql`](sample-data.sql)  
Use the SQL file to seed the MySQL database.

This set covers:

- Multiple quiz questions
- Four answer choices for each question
- All four personality types
- Answers mapped to personality types
- Multiple completed quiz results
- Repeated personality results across different quiz attempts

---

## Personality types

| personality_type_ID | personality_type | description |
|---------------------|------------------|-------------|
| 1 | Orange | Energetic, spontaneous, and action-oriented |
| 2 | Gold | Organized, dependable, and structured |
| 3 | Green | Analytical, curious, and independent |
| 4 | Blue | Compassionate, cooperative, and relationship-focused |

---

## Questions

| question_ID | question_text |
|-------------|---------------|
| 1 | Which activity sounds most appealing? |
| 2 | How do you usually approach a new problem? |
| 3 | What do you value most when working in a group? |
| 4 | Which environment do you prefer? |
| 5 | What best describes how you make decisions? |

---

## Answers

### Question 1 — Which activity sounds most appealing?

| answer_ID | question_ID | answer_text | personality_type_ID |
|-----------|-------------|-------------|---------------------|
| 1 | 1 | Trying something exciting and spontaneous | 1 |
| 2 | 1 | Planning and completing an organized project | 2 |
| 3 | 1 | Learning how something complex works | 3 |
| 4 | 1 | Spending meaningful time with other people | 4 |

### Question 2 — How do you usually approach a new problem?

| answer_ID | question_ID | answer_text | personality_type_ID |
|-----------|-------------|-------------|---------------------|
| 5 | 2 | Jump in and adjust as I go | 1 |
| 6 | 2 | Make a clear step-by-step plan | 2 |
| 7 | 2 | Analyze the problem before acting | 3 |
| 8 | 2 | Talk it through with others | 4 |

### Question 3 — What do you value most when working in a group?

| answer_ID | question_ID | answer_text | personality_type_ID |
|-----------|-------------|-------------|---------------------|
| 9 | 3 | Energy and flexibility | 1 |
| 10 | 3 | Organization and responsibility | 2 |
| 11 | 3 | Logic and strong ideas | 3 |
| 12 | 3 | Cooperation and understanding | 4 |

### Question 4 — Which environment do you prefer?

| answer_ID | question_ID | answer_text | personality_type_ID |
|-----------|-------------|-------------|---------------------|
| 13 | 4 | A fast-paced environment with variety | 1 |
| 14 | 4 | A predictable environment with clear expectations | 2 |
| 15 | 4 | A quiet environment where I can focus | 3 |
| 16 | 4 | A friendly environment with lots of interaction | 4 |

### Question 5 — What best describes how you make decisions?

| answer_ID | question_ID | answer_text | personality_type_ID |
|-----------|-------------|-------------|---------------------|
| 17 | 5 | I decide quickly and trust my instincts | 1 |
| 18 | 5 | I follow rules and proven methods | 2 |
| 19 | 5 | I compare facts and possibilities | 3 |
| 20 | 5 | I consider how the decision affects people | 4 |

---

## Quiz results

| results_ID | personality_type_ID | completed_date | person_ID |
|------------|---------------------|----------------|-----------|
| 1 | 3 | 2026-09-14 | 1001 |
| 2 | 2 | 2026-09-15 | 1002 |
| 3 | 4 | 2026-09-16 | 1003 |
| 4 | 1 | 2026-09-17 | 1004 |
| 5 | 3 | 2026-09-18 | 1005 |

The sample results include at least one completed quiz for every personality type. Green appears twice so cumulative statistics can demonstrate that more than one quiz attempt may produce the same result.
