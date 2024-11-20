# Test Plan for Numble

---

## 1. Boundary Cases

- **Number of Players**:  
  - Minimum number of players: 1  
  - Maximum number of players: 2  
  - Test what happens if a player is disconnected from the server during a round.  

- **Lives**:  
  - Verify that if a player runs out of lives, the game properly restarts.  
  - In a two-player lobby, ensure that if one player runs out of lives, they are awarded a point for the round.  

- **Round Completion**:  
  - In a two-player lobby, test if the game ends correctly when one player reaches the required number of points or loses all their lives. Verify that both players can disconnect without errors.  
  - In a single-player mode, confirm that when a round ends, the player is presented with options to restart or exit. Ensure that the round's data is properly stored and pushed to the global leaderboard.  

---

## 2. Design Integration

- **Lives and Global Leaderboard**:  
  - Test that lives are subtracted correctly with each incorrect number guess.  
  - Ensure that the game ends and eliminates remaining lives when the round concludes.  
  - Verify that when the round ends, the stopwatch records the total playtime, and the data is correctly submitted to the global leaderboard.  
  - Ensure the global leaderboard updates accurately with the latest data and refreshes automatically every minute.  

---

## 3. Logic in Numble

- **Numble / Wordle Features**:  
  - Confirm that the numbers change color appropriately based on how they align with the current guess.  
  - Verify that when a correct number is picked, the number changes color, awards points in multiplayer, or declares a win in single-player mode.  
  - Ensure that the hidden number is randomized for every round and does not repeat unnecessarily.  

- **Logic Errors**:  
  - Verify that the timer updates accurately throughout the round.  
  - Confirm that lives are calculated and subtracted correctly during gameplay.  
  - Ensure the game runs smoothly without any glitches or delays.  
  - Validate that round information aligns correctly with leaderboard statistics.  

---

## 4. Protect Execution from Bad Input

- **Invalid Key Presses**:  
  - Ensure the game does not break if a player tries to input a number outside the valid range.  
  - Confirm that negative numbers are not allowed as valid inputs.  
  - Protect the leaderboard from being tampered with or artificially inflated.  

- **Non-Numeric Input**:  
  - Verify that account passwords are securely stored when entered.  
  - Ensure long player names or special characters are restricted to avoid UI disruption.  

---

## 5. Handle Other Run-Time Errors

- **Full Screen Handling**:  
  - Ensure that the game ends gracefully with a "Game Over" message when the screen or area is filled.  
  - Test the game’s behavior when nearing a filled state to ensure no crashes or freezes occur.  

- **Error Handling at High Speed**:  
  - Validate that the game remains responsive and fluid at higher speeds or levels.  
  - Test for potential crashes caused by excessive frame rates or memory overload during fast gameplay.  

- **Recovery from Errors**:  
  - Verify that corrupted save files notify the player with an appropriate message (e.g., "Save file is corrupted. Starting a new game.").  
  - Ensure that server disconnections redirect players to the main menu without breaking the game.  
  - Confirm that rejoining a multiplayer lobby after a disconnection is seamless and maintains game progress where possible.  

---

## 6. Test Case Table

| **Test Case**             | **Test Data**                             | **Expected Outcome**                                         |
|---------------------------|-------------------------------------------|-------------------------------------------------------------|
| Player input validation    | Invalid numbers (e.g., -1, 999)          | The game displays an error: "Please enter a valid number."   |
| Movement boundaries        | Actions near the edge of the play area   | Players cannot move beyond the boundary; no crashes occur.   |
| Speed increase             | Reaching higher levels or milestones     | Game speeds up progressively and remains playable.           |
| Score calculation          | Clearing objectives or winning rounds    | Scores increase accurately based on gameplay actions.        |
| Turn switching             | Player 1 completes a turn in multiplayer | The game switches turns to Player 2 seamlessly.              |
| Game Over handling         | Running out of lives in single-player    | The game displays a "Game Over" message and stores results.  |
| Bonus trigger              | Special scenarios triggering bonuses     | Bonuses activate correctly and resume normal gameplay.       |
| Leaderboard update         | Achieving a new high score               | The leaderboard updates with accurate player data.           |
| Timer functionality        | Completing a round in single-player      | The timer stops and records the playtime accurately.         |
| Save/Load behavior         | Saving/loading game state                | The game state is saved and loaded without errors.           |

---
