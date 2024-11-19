# Pseudocode For Numble

## Start of Game

### Process:
1. Display welcome message: **"Welcome to Numble!"**
2. Display game options:
   - **1.** Play Single-Player
   - **2.** Play Multiplayer Mode
   - **3.** View Leaderboard
3. **Option Prompt**:
   - If user picks option **1**:
     - Call the `singleplayer()` function.
   - Else if user picks option **2**:
     - Call the `multiplayer()` function.
   - Else:
     - Call the `leaderboard()` function.

---

## Singleplayer

### `singleplayer()`

#### Process:
1. Display singleplayer rules for how to play.
2. Set `hidden_number = random number between 1 and 100`.
3. Initialize `attempts = 0`.
4. Start the game stopwatch.

#### Gameplay Loop:
- **While the player has not guessed correctly**:
  1. Prompt user: **"Enter your guess."**
  2. Increment `attempts` by 1.
  3. Check the guess:
     - If `player_guess < hidden_number`:
       - Display: **"Too low! Try a higher number."**
     - Else if `player_guess > hidden_number`:
       - Display: **"Too high! Try a lower number."**
     - Else:
       - Display: **"Congratulations! You guessed correctly."**
       - Stop the game stopwatch.
       - Record the player's attempts and time.
       - Update the leaderboard.
       - Display options:
         - **"Return to main menu, try again, or join multiplayer."**
         - If the user selects **"try again"**:
           - Restart the game.
         - Else if the user selects **"main menu"**:
           - Return to the main menu.
         - Else:
           - Join multiplayer server.

---

## Multiplayer

### `multiplayer()`

#### Process:
1. Display multiplayer rules for how to play.
2. Set the grid of hidden numbers.
3. Wait for **Player 1** and **Player 2** to connect.
4. Once both players are connected:
   - Initialize Player 1 in the server.
   - Initialize Player 2 in the server.
   - Initialize `Player 1's attempts = 0`.
   - Initialize `Player 2's attempts = 0`.
   - Set `hidden_number = random number between 1 and 100`.

#### Gameplay Loop:
- Randomly select which player goes first.
- **While the game is active (10 rounds total)**:
  1. **If it is Player 1's turn**:
     - Prompt Player 1: **"Enter your guess."**
     - Check the guess:
       - If correct:
         - Award 1 point to Player 1.
         - Announce: **"Correct guess! Player 1 scores a point!"**
         - Generate a new hidden number for the next round.
       - Else:
         - Announce: **"Wrong guess! No points awarded."**
         - Display a hint (e.g., **"Too low"** or **"Too high"**).
  2. **If it is Player 2's turn**:
     - Prompt Player 2: **"Enter your guess."**
     - Check the guess:
       - If correct:
         - Award 1 point to Player 2.
         - Announce: **"Correct guess! Player 2 scores a point!"**
         - Generate a new hidden number for the next round.
       - Else:
         - Announce: **"Wrong guess! No points awarded."**
         - Display a hint (e.g., **"Too low"** or **"Too high"**).

#### End of Game:
1. **After 10 rounds**:
   - Compare `Player 1's score` and `Player 2's score`.
   - Announce the winner:
     - **"Player X wins!"** or **"It's a tie!"** if scores are equal.
2. Offer options:
   - **"Play again or return to the main menu."**
   - If **"play again"** is selected:
     - Restart multiplayer mode.
   - Else:
     - Return to the main menu.

---

## Leaderboard

### `leaderboard()`

#### Data Structure:
```plaintext
leaderboard_data = [
    {"Player Name": "Alice", "Score": 15, "Time": "2:35"},
    {"Player Name": "Bob", "Score": 10, "Time": "3:10"},
    {"Player Name": "Charlie", "Score": 5, "Time": "5:00"}
]
