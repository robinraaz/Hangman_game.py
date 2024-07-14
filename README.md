# Hangman_game.py
import random
def hangman():
    # List of words
    words = ['python', 'programming', 'hangman', 'challenge', 'interpreter', 'random', 'guess']
    # Choose a random word
    word = random.choice(words)
    word_length = len(word)
    guessed_word = ['_'] * word_length
    attempts = 12  # Number of turns, can be adjusted
    # Input player's name
    player_name = input("Enter your name: ")
    print(f"Hello {player_name}! Let's start the game of Hangman.")
    print(' '.join(guessed_word))
    while attempts > 0:
        guess = input("Guess an alphabet: ").lower()
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter a single valid alphabet.")
            continue
        if guess in word:
            for i in range(word_length):
                if word[i] == guess:
                    guessed_word[i] = guess
            print("Good guess!")
        else:
            attempts -= 1
            print(f"Wrong guess! You have {attempts} attempts left.")
        print(' '.join(guessed_word))
        if '_' not in guessed_word:
            print(f"Congratulations {player_name}! You guessed the word '{word}' correctly.")
            break
    else:
        print(f"Sorry {player_name}, you ran out of attempts. The word was '{word}'.")
# Run the game
hangman()
