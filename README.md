# codealpha_tasks

Task 1: Hangman Game
A text-based console game where players guess a hidden word letter-by-letter with a limit of 6 incorrect attempts. Built using standard Python loops, conditionals, and random word selection.

import random

# List of words
words = [
    "python",
    "computer",
    "program",
    "developer",
    "security"
]

# Hangman stages
hangman_stages = [
    """
     +---+
     |   |
         |
         |
         |
         |
    =========
    """,
    """
     +---+
     |   |
     O   |
         |
         |
         |
    =========
    """,
    """
     +---+
     |   |
     O   |
     |   |
         |
         |
    =========
    """,
    """
     +---+
     |   |
     O   |
    /|   |
         |
         |
    =========
    """,
    """
     +---+
     |   |
     O   |
    /|\\  |
         |
         |
    =========
    """,
    """
     +---+
     |   |
     O   |
    /|\\  |
    /    |
         |
    =========
    """,
    """
     +---+
     |   |
     O   |
    /|\\  |
    / \\  |
         |
    =========
    """
]


def play_hangman():
    word = random.choice(words)
    guessed_letters = []
    wrong_guesses = 0
    max_attempts = 6

    print("\n===== HANGMAN GAME =====")
    print("Guess the word before the man is hanged!")
    print("You have 6 wrong attempts.")

    while wrong_guesses < max_attempts:

        # Display current word
        display_word = ""

        for letter in word:
            if letter in guessed_letters:
                display_word += letter + " "
            else:
                display_word += "_ "

        print("\nWord:", display_word)
        print("Guessed letters:", " ".join(guessed_letters))
        print(hangman_stages[wrong_guesses])

        # Check if word is completely guessed
        if all(letter in guessed_letters for letter in word):
            print("Congratulations! You guessed the word:", word)
            return

        # Take user input
        guess = input("Enter a letter: ").lower()

        # Validate input
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter only one alphabetic letter.")
            continue

        if guess in guessed_letters:
            print("You already guessed that letter.")
            continue

        guessed_letters.append(guess)

        # Check guess
        if guess in word:
            print("Correct guess!")
        else:
            wrong_guesses += 1
            print("Wrong guess!")

    # Game over
    print(hangman_stages[wrong_guesses])
    print("Game Over!")
    print("The correct word was:", word)


# Main program
while True:
    play_hangman()

    choice = input("\nDo you want to play again? (yes/no): ").lower()

    if choice != "yes":
        print("Thank you for playing Hangman!")
        break

Task 2: Basic Chatbot
A rule-based command-line chatbot that listens to basic user inputs (like "hello" or "bye") and responds with preset replies. Uses simple if-elif logic, loops, and custom functions to manage the conversation.

def chatbot(user_input):
    user_input = user_input.lower()

    if user_input == "hello":
        return "Hi!"

    elif user_input == "how are you":
        return "I'm fine, thanks!"

    elif user_input == "bye":
        return "Goodbye!"

    else:
        return "Sorry, I don't understand."


print("Chatbot: Hello! Type 'bye' to exit.")

while True:
    user_input = input("You: ")

    reply = chatbot(user_input)
    print("Chatbot:", reply)

    if user_input.lower() == "bye":
        break       
