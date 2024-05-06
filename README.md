# Practice-Python-45---Quiz-Game

import random


class QuizGame:
    def __init__(self):
        self.questions = {
            "Python": [
                {"question": "What is the capital of Python?", "options": ["Monty", "Snakeville", "Pyland", "Python City"], "correct_answer": "Monty"},
                {"question": "Which of the following is not a Python data type?", "options": ["int", "float", "boolean", "double"], "correct_answer": "double"},
                {"question": "What is the correct way to comment multiple lines in Python?", "options": ["/* Comment */", "// Comment", "''' Comment '''", "# Comment"], "correct_answer": "# Comment"},
                {"question": "Which of the following data types is immutable in Python?", "options": ["List", "Tuple", "Set", "Dictionary"], "correct_answer": "Tuple"}
            ],
            "General Knowledge": [
                {"question": "What is the largest mammal in the world?", "options": ["Elephant", "Whale Shark", "Blue Whale", "Giraffe"], "correct_answer": "Blue Whale"},
                {"question": "Which planet is known as the Red Planet?", "options": ["Earth", "Mars", "Venus", "Jupiter"], "correct_answer": "Mars"},
                {"question": "What is the capital of Australia?", "options": ["Sydney", "Perth", "Melbourne", "Canberra"], "correct_answer": "Canberra"},
                {"question": "who is discoverer of Polonium?", "options": ["Marie Curie", "Pirre Curie", "Both", "Einstein"], "correct_answer": "Both"},
                {"question": "What is the largest ocean on Earth?", "options": ["Atlantic Ocean", "Indian Ocean", "Pacific Ocean", "Arctic Ocean"], "correct_answer": "Pacific Ocean"},
                {"question": "What is the capital city of Japan?", "options": ["Seoul", "Beijing", "Tokyo", "Bangkok"], "correct_answer": "Tokyo"},
                {"question": "Who wrote the play 'Romeo and Juliet'?", "options": ["Charles Dickens", "William Shakespeare", "Jane Austen", "Mark Twain"], "correct_answer": "William Shakespeare"},
                {"question": "In which year did the first manned moon landing occur?", "options": ["1965", "1969", "1973", "1981"], "correct_answer": "1969"},
            ],
        }
        self.score = 0

    def get_user_choice(self, options):
        print("Options:")
        for i, option in enumerate(options, start=1):
            print(f"{i}. {option}")

        while True:
            try:
                choice = int(input("Enter the number corresponding to your answer: "))
                if 1 <= choice <= len(options):
                    return options[choice - 1]
                else:
                    print("Invalid choice. Please enter a valid number.")
            except ValueError:
                print("Invalid input. Please enter a number.")

    def play_quiz(self):
        print("Welcome to the Quiz Game!")
        for category, questions in self.questions.items():
            print(f"\nCategory: {category}")
            for question_data in questions:
                print("\n" + question_data["question"])
                user_answer = self.get_user_choice(question_data["options"])
                correct_answer = question_data["correct_answer"]

                if user_answer == correct_answer:
                    print("Correct!\n")
                    self.score += 1
                else:
                    print(f"Wrong! The correct answer is: {correct_answer}\n")

        self.display_results()

    def display_results(self):
        print("\nQuiz Completed!")
        print(f"Your Score: {self.score}/{len(self.questions['Python'] + self.questions['General Knowledge'])}")


if __name__ == "__main__":
    quiz_game = QuizGame()
    quiz_game.play_quiz()
