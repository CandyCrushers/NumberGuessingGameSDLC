# Pseudocode For Numble

## Start of Game
- Display welcome message: **"Welcome to Numble!"**
- Display game options:
  1. Play Single-Player
  2. Play Multiplayer Mode
  3. View Leaderboard

- **Option Prompt**:
  - If user picks option 1:
    - Call the `singleplayer` function.
  - Else if user picks option 2:
    - Call the `multiplayer` function.
  - Else:
    - Call the `leaderboard` function.

---

## Singleplayer

### `singleplayer()`
1. Display singleplayer rules for how to play.
2. Set `hidden_number` = random number between 1 and 100.
3. Initialize `attempts` = 0.
4. Start the game stopwatch.

5. **While the player has not guessed correctly**:
   - Prompt user: **"Enter your guess."**
   - Increment `attempts` by 1.
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
1. Display multiplayer rules for how to play.
2. Set the grid of hidden numbers.
3. Wait for **Player 1** and **Player 2** to connect.
4. Once both players are connected:
   - Initialize Player 1 in the server.
   - Initialize Player 2 in the server.
   - Initialize `Player 1's attempts` = 0.
   - Initialize `Player 2's attempts` = 0.
   - Set `hidden_number` = random number between 1 and 100.

5. Randomly select which player goes first.

6. **While the game is active (10 rounds total)**:
   - **If Player 1's turn**:
     - Prompt Player 1: **"Enter your guess."**
     - If Player 1 guesses correctly:
       - Award 1 point to Player 1.
       - Announce: **"Correct guess! Player 1 scores a point!"**
       - Generate a new hidden number for the next round.
     - Else:
       - Announce: **"Wrong guess! No points awarded."**
       - Display a hint (e.g., **"Too low"** or **"Too high"**).

   - **If Player 2's turn**:
     - Prompt Player 2: **"Enter your guess."**
     - If Player 2 guesses correctly:
       - Award 1 point to Player 2.
       - Announce: **"Correct guess! Player 2 scores a point!"**
       - Generate a new hidden number for the next round.
     - Else:
       - Announce: **"Wrong guess! No points awarded."**
       - Display a hint (e.g., **"Too low"** or **"Too high"**).

7. **After 10 rounds**:
   - Compare `Player 1's score` and `Player 2's score`.
   - Announce the winner:
     - **"Player X wins!"** or **"It's a tie!"** if scores are equal.
   - Offer options:
     - **"Play again or return to the main menu."**
   - If **"play again"** is selected:
     - Restart multiplayer mode.
   - Else:
     - Return to the main menu.

---

## Leaderboard

### `leaderboard()`
1. **Data Structure**:
   ```plaintext
   leaderboard_data = [
       {"Player Name": "Alice", "Score": 15, "Time": "2:35"},
       {"Player Name": "Bob", "Score": 10, "Time": "3:10"},
       {"Player Name": "Charlie", "Score": 5, "Time": "5:00"}
   ]
