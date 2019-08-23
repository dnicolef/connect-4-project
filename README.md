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
// let x, y;
function play(position, playerId){
  let x, y;
  for(let i = 0; i < count; i++){
    // check if the current cell is empty (0 for empty)
    if(board[i][position] == 0){
      // update the current cell to 1 for player 1
      board[i][position] = playerId;
      // clear the row before if we are not on the first row
      if(i !== 0){
        board[i-1][position] = 0;
      }
      
    }else{ //printing the last position of the disc if the columns already has dics in it
      x = i - 1;
      y = position;
      break;
    }
    //Printing the last position of the dics if the previous attemps has not been successful (this is useful for the bottom, when the columns is still empty)
    if(i== count - 1){
      x = i;
      y = position;
    }
  }
  return(`${x},${y}`);
}

console.log(play(0, 1));
console.log(play(0, 1));
console.log(play(0, 1));
console.log(play(0, 1));
play(1, 1);
play(2, 1)
console.log(play(3, 1))
// console.log(play(6, 1).split(',')[0]);

console.log(board);

checkForWin(5, 3);

function checkForWin(x, y){
  let b = board[x][y];
  console.log(b)
  if(y > 2){
    if(board[x][y-1] == b && board[x][y-2] == b && board[x][y-3] == b){
      if(b){
        return('win');
      }
    }
  }
  if(y > 2 && x < 3){
    if(board[x+1][y-1] == b && board[x+2][y-2] == b && board[x+3][y-3] == b){
      if(b){
        return('win');
      }
    }
  }
  if(x < 3){
    if(board[x+1][y] == b && board[x+2][y] == b && board[x+3][y] == b){
      if(b){
        return('win');
      }
    }
  }
  if(x < 3 && y < 4){
    if(board[x+1][y+1] === b && board[x+2][y+2] === b && board[x+3][y+3] === b){
      if(b){
        return('win');
      }
    }
  }
  if(y < 4){
    if(board[x][y+1] == b && board[x][y+2] == b && board[x][y+3] == b){
      if(b){
        return('win');
      }
    }
  }
  return('lost')
}
```
**Checking for winning combination after each play**

```
if(y > 2) //case 1
  check position(x)(y) == position(x)(y-1) == position(x)(y-2) == position(x)(y-3)
if(y > 2 and x < 3) //case 2
  check position(x)(y) == position(x+1)(y-1) == position(x+2)(y-2) == position(x+3)(y-3)
if(x < 3) //case 3
  check position(x)(y) == position(x+1)(y) == position(x+2)(y) == position(x+3)(y)
if(x < 3 and y < 4) //case 4
  check position(x)(y) == position(x+1)(y+1) == position(x+2)(y+1) == position(x+3)(y+1)
if(y < 4) //case 5
  check position(x)(y) == position(x)(y+1) == position(x)(y+2) == position(x)(y+3)
```
case 1

![image 1](https://raw.githubusercontent.com/dnicolef/connect-4-project/master/leftward.PNG)

case 2

![image 1](https://raw.githubusercontent.com/dnicolef/connect-4-project/master/downward.PNG)

case 3

![image 1](https://raw.githubusercontent.com/dnicolef/connect-4-project/master/leftleft.PNG)

case 4

![image 1](https://raw.githubusercontent.com/dnicolef/connect-4-project/master/rightright.PNG)

case 5

![image 1](https://raw.githubusercontent.com/dnicolef/connect-4-project/master/rightward.PNG)
