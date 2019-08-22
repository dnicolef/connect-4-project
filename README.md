# connect-4-project
Connect 4 game Project 

### User Stories

1. The user should be able to play against the computer
2. The user should be able to see the number of Games he’s played
3. The user should be able to see his/her total point count
4. The game should tell the player who won the game after it is over.


### Logic
**Most Basic Filling the Board**
```
let board = [
  [0, 0, 0, 0, 0, 0, 0], 
  [0, 0, 0, 0, 0, 0, 0], 
  [0, 0, 0, 0, 0, 0, 0], 
  [0, 0, 0, 0, 0, 0, 0], 
  [0, 0, 0, 0, 0, 0, 0], 
  [0, 0, 0, 0, 0, 0, 0]
];

let count = 6; //number of columns

// position goes from 0 to 6 (1 to 7 in the real world. Each position corresponting to a position in the row)
// playerId can be set to 1 for the first player and 2 for the second player

function play(position, playerId){
  for(let i = 0; i < count; i++){
    // check if the current cell is empty (0 for empty)
    if(board[i][position] == 0){
      // update the current cell to 1 for player 1
      board[i][position] = playerId;
      // clear the row before if we are not on the first row
      if(i !== 0){
        board[i-1][position] = 0;
      }
    }
  }
  return board; 
}

play(6, 1);
play(2, 2);
play(5, 1);
play(2, 2);
play(2, 1);
play(0, 2);
play(0, 1);
play(6, 2);
play(5, 1);
play(2, 2);
play(3, 1);
play(0, 2);
play(3, 1);
play(5, 2);
```
Output
```
=> [ 
  [ 0, 0, 0, 0, 0, 0, 0 ],
  [ 0, 0, 0, 0, 0, 0, 0 ],
  [ 0, 0, 2, 0, 0, 0, 0 ],
  [ 2, 0, 1, 0, 0, 2, 0 ],
  [ 1, 0, 2, 1, 0, 1, 2 ],
  [ 2, 0, 2, 1, 0, 1, 1 ] ]
```
**Checking for winning combination after each play**

(To do...)
