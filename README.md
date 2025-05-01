def hangman():

    # List of words that should be guessed 
    
    words = ["list", "programming", "incorrect","information", "development", "challenge", "technology"]
    
    # Randomly select a word
    
    word = random.choice(words).lower()
    letters = set(word)  # Unique letters in the word
    guessed_letters = set()
    wrong_guess = set()
    
    # Set the maximum number of incorrect guesses
    num_tries = 7
    
    print("Welcome to Hangman Game!")
    print(f"I'm thinking of a word that has {len(word)} letters.")
    print(f"You have {num_tries} incorrect guesses allowed.\n")
    
    while len(wrong_guess) < num_tries and not letters.issubset(guessed_letters):
        # Display current state of the word
        display_word = [letter if letter in guessed_letters else '_' for letter in word]
        print("Current word: " + ' '.join(display_word))
        print(f"Wrong guesses ({len(wrong_guess)}/{num_tries}): " + ', '.join(sorted(wrong_guess)))
        
        # Get user input
        guess = input("Guess a letter: ").lower()
        
        # Validate input
        if len(guess) != 1 or not guess.isalpha():
            print("Please enter one letter of the alphabet\n")
            continue
        
        if guess in guessed_letters or guess in wrong_guess:
            print("You already guessed that letter. Please try again.\n")
            continue
        
        # Check if guess is correct
        if guess in letters:
            guessed_letters.add(guess)
            print(f"Excellent! '{guess}' is in the word.\n")
        else:
            wrong_guess.add(guess)
            print(f"Sorry, '{guess}' is not in the word.\n")
    
    # Check if the player has won or lost
    if letters.issubset(guessed_letters):
        print(f"Congratulations! You guessed the correct word: {word}")
    else:
        print(f"Game over! You've used all your guesses. The word was: {word}")

# Run the game
if __name__ == "__main__":
    hangman()


How it works:
* The program picks a random word.
* The player guesses one letter at a time.
* The game displays the current state of the word with underscores for unguessed letters.
* The player has a limited number of incorrect guesses (7 in this case).
* The game ends when the player guesses all the letters or runs out of guesses.
