# Pseudocode For Numble

## Start of Game

Display "Welcome to Numble!"
Display options:
    1. Play Single-Player
    2. Play Multiplayer Mode
    3. View Leaderboard

Prompt user to select an option.
if option == 1:
    call singleplayer()
elif option == 2:
    call multiplayer()
else:
    call leaderboard()

---

## Singleplayer

singleplayer():
    Display "Singleplayer Rules: Guess the number between 1 and 100."
    hidden_number = random number between 1 and 100
    attempts = 0
    Start game stopwatch

    while player has not guessed correctly:
        Display "Enter your guess:"
        player_guess = input
        attempts += 1
        if player_guess < hidden_number:
            Display "Too low! Try a higher number."
        elif player_guess > hidden_number:
            Display "Too high! Try a lower number."
        else:
            Display "Congratulations! You guessed correctly!"
            Stop game stopwatch
            Record attempts and time
            Update leaderboard
            Display options:
                1. Return to Main Menu
                2. Try Again
                3. Join Multiplayer
            if option == 2:
                Restart game
            elif option == 1:
                Return to Main Menu
            else:
                Join Multiplayer

---

## Multiplayer

multiplayer():
    Display "Multiplayer Rules: Guess the hidden number before your opponent."
    Set up hidden grid of numbers
    Wait for Player 1 and Player 2 to connect
    Initialize Player 1 and Player 2 in the server
    Player 1 attempts = 0
    Player 2 attempts = 0
    hidden_number = random number between 1 and 100

    Randomly select first player

    while rounds < 10:
        if current_turn == Player 1:
            Display "Player 1, enter your guess:"
            player_guess = input
            if player_guess == hidden_number:
                Award 1 point to Player 1
                Display "Player 1 guessed correctly and scores a point!"
                Generate new hidden_number
            else:
                Display "Incorrect guess. No points awarded."
                Display hint ("Too low" or "Too high")
            Switch turn to Player 2

        else:
            Display "Player 2, enter your guess:"
            player_guess = input
            if player_guess == hidden_number:
                Award 1 point to Player 2
                Display "Player 2 guessed correctly and scores a point!"
                Generate new hidden_number
            else:
                Display "Incorrect guess. No points awarded."
                Display hint ("Too low" or "Too high")
            Switch turn to Player 1

    Compare scores:
        if Player 1 score > Player 2 score:
            Display "Player 1 wins!"
        elif Player 2 score > Player 1 score:
            Display "Player 2 wins!"
        else:
            Display "It's a tie!"

    Display options:
        1. Play Again
        2. Return to Main Menu
    if option == 1:
        Restart multiplayer()
    else:
        Return to Main Menu

---

## Leaderboard

leaderboard():
    Display "====== LEADERBOARD ======"
    Display "Rank | Player Name | Score | Time Taken"

    Sort leaderboard_data by Score in descending order
    for player in leaderboard_data:
        Display rank, player["Name"], player["Score"], player["Time"]

    Display options:
        1. Return to Main Menu
        2. Reset Leaderboard
    if option == 2:
        leaderboard_data = []
        Display "Leaderboard reset successfully."
    else:
        Return to Main Menu
