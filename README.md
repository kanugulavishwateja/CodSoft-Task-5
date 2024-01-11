import random

def load_quiz_questions():
    # Define your quiz questions, options, and correct answers
    quiz_questions = [
        {
            'question': 'What is the capital of France?',
            'options': ['A. Berlin', 'B. Paris', 'C. Rome', 'D. Madrid'],
            'correct_answer': 'B'
        },
        {
            'question': 'Which planet is known as the Red Planet?',
            'options': ['A. Venus', 'B. Mars', 'C. Jupiter', 'D. Saturn'],
            'correct_answer': 'B'
        },
        {
            'question': 'What is the largest mammal on Earth?',
            'options': ['A. Elephant', 'B. Blue Whale', 'C. Giraffe', 'D. Gorilla'],
            'correct_answer': 'B'
        }
        # Add more questions as needed
    ]

    return quiz_questions

def display_welcome_message():
    print("Welcome to the Quiz Game!")
    print("You will be asked multiple-choice questions on different topics.")
    print("Choose the correct answer for each question. Let's get started!\n")

def present_quiz_question(question):
    print(question['question'])
    for option in question['options']:
        print(option)
    user_answer = input("Your answer: ").upper()
    return user_answer

def evaluate_user_answer(user_answer, correct_answer):
    if user_answer == correct_answer:
        print("Correct! Well done.")
        return True
    else:
        print(f"Incorrect. The correct answer is {correct_answer}.")
        return False

def calculate_final_score(score, total_questions):
    percentage = (score / total_questions) * 100
    return percentage

def display_final_results(score, total_questions):
    print("\nQuiz Completed!")
    print(f"Your final score: {score}/{total_questions} ({calculate_final_score(score, total_questions):.2f}%)")

def play_again():
    return input("Do you want to play again? (yes/no): ").lower() == 'yes'

def main():
    quiz_questions = load_quiz_questions()
    total_questions = len(quiz_questions)
    score = 0

    while True:
        display_welcome_message()

        for question in random.sample(quiz_questions, total_questions):
            user_answer = present_quiz_question(question)
            if evaluate_user_answer(user_answer, question['correct_answer']):
                score += 1

        display_final_results(score, total_questions)

        if not play_again():
            print("Thank you for playing! Goodbye!")
            break
        else:
            score = 0  # Reset the score for a new game

if __name__ == "__main__":
    main()

