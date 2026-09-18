# Use cases

This system lets anyone take a fixed 30-question multiple-choice personality quiz based on the True Colors test, and view their personal results and cumulative statistics from all quiz takers' completed quiz attempts afterwards. The same person may take the quiz more than once, since there is no login.
Before beginning the quiz, the user enters a name. When the quiz begins, the system creates a unique quiz ID so that the user's quiz attempt can be tracked between the quiz and results pages. The entire quiz is shown on one page rather than showing one question at a time.
Each answer corresponds to one personality category and contributes points toward that category. After all questions are answered and the quiz is submitted, the system totals the points for each personality category. The category with the highest score becomes the user's personality result.
Completed quiz results are also included in cumulative statistics showing how personality results are distributed across all completed quiz attempts.

---

## Welcome View

Someone opens the application and sees an introduction page explaining the quiz's topic and how to take it. The page provides a way to begin the quiz.

### Scenarios

- **Open application** — The user opens the application and sees information explaining the personality quiz.
- **Start quiz** — The user chooses to start the quiz by selecting the button for it.

---

## Input Name

They enter their name at the top of the quiz. The name is used for the current quiz attempt but is not used to create an account or sign the user in.
When the user continues, the system creates a unique quiz attempt ID. The attempt ID allows the application to associate the user's quiz answers with a personality type result.

### Scenarios

- **Present Input** — The user is required to enter a name in a text box. The system allows the quiz to submit successfully.
- **Missing name** — The user attempts to continue without entering a name. The quiz does not submit, and the user is told that a name is required.

---

## Take the Quiz

Someone starts a quiz attempt. They will see all the quiz questions together on one page. Each question contains 4 multiple-choice answers. The user selects one answer for each question. Each answer corresponds to one personality category and contributes points toward that category. The system associates the answers with a quiz attempt ID created upon submission.

### Scenarios

- **Quiz page** — The user sees all personality questions and their available multiple-choice answers on one page.
- **Select answers** — The user selects one answer for each question.
- **Change an answer** — Before submitting the quiz, the user may select a different answer for a question.

---

## Submit the Quiz

Someone has answered all of the quiz questions and wants to receive their personality result. They can only submit the quiz after selecting an answer for every question. If one or more questions have not been answered, the quiz is not submitted. The user remains on the unchanged quiz page and is told that all questions must be answered to continue to results.
The system calculates the points contributed by each answer and totals the points for each personality category. The personality category with the highest score becomes the result for that quiz attempt.
The completed result is saved so that it can be displayed on the user's personal results page and included in the application's cumulative statistics.



### Scenarios

- **Successful submission** — Every question has a selected answer. The system calculates the scores for each category and determines which is highest, saves the personality result, and opens the personal results page.
- **Incomplete quiz** — One or more questions are unanswered. The quiz is not submitted, and the user is told that every question must be answered.

---

## View Personality Results 

Someone has completed the quiz and wants to see their personal result. They see their name, their assigned personality category, and a description explaining that personality type. The result corresponds to the quiz attempt that they just completed.
The personal results page also provides a way to open the overall statistics page and see how the user's result compares with results from all completed quiz attempts.

### Scenarios

- **View personal result** — The user sees their name, personality category, and a description of that personality type.
- **Open overall statistics** — The user chooses to view cumulative quiz statistics and is taken to the statistics page.

---

## View Overall Statistics

Someone wants to see how personality results are distributed across everyone who has completed the quiz. They open the statistics page from their personal results page.
The system uses all completed stored quiz attempts to calculate the cumulative results. The page shows each personality category and the percentage of completed quiz attempts assigned to that category. 

### Scenarios

- **View statistics** — The user sees the percentage of completed quiz attempts belonging to each personality category.
- **Accumulate overall results** — When additional quizzes are completed, those results are included in future statistics.

---

## Personality Scoring

Each multiple choice answer of a given question of the quiz belongs to 1 of 4 personality categories: Blue, green, yellow, orange. When a quiz is submitted, the system totals the points associated with the selected answers for each category and selects the highest score as the user's personality.

### Scenarios

- **One highest category** — One category has more totalled points than every other category. That category becomes the displayed personality result.
- **Score calculation** — Each selected answer contributes its summed points to the associated personality category.
- **Tie between categories** — If two or more categories have the same highest score, the results page will display both categories and announce a tie. 

---

## Cumulative Statistics Calculation

The system stores cumulative information about all completed quiz attempts. Each successfully submitted quiz contributes one personality result to the cumulative results. These results are then used to produce the overall statistics page.
This report is based only on completed quiz attempts. Quiz attempts that were started but never submitted are not included.

### Scenarios

- **Completed attempt included** — After a quiz is successfully submitted, its personality category is included in cumulative results.
- **Incomplete attempt excluded** — A quiz that was started but never submitted does not affect the cumulative statistics.
- **Handling tie personality result** – If a quiz attempt results in a user having a tie between two or more categories, a point will go to each category that the tie is a part of.
- **Updated report** — When another quiz is completed, the cumulative result totals and percentages reflect the new result.
