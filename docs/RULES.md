# TicTacToe: Hidden Stakes - Game Rules

## Overview

TicTacToe: Hidden Stakes is a variant of classic tic-tac-toe where draws are mathematically impossible. Players win by either getting three-in-a-row OR accumulating the most points when the board fills.

## The Board

```
2 | 1 | 2
---------
1 | 3 | 1
---------
2 | 1 | 2
```

Each cell has a point value:
- **Center cell**: 3 points
- **Corner cells** (4 total): 2 points each
- **Edge cells** (4 total): 1 point each

## How to Play

1. **Players**: Two players, X and O
2. **Turn order**: X plays first, then players alternate
3. **On your turn**: Click any empty cell to place your piece
4. **Claiming points**: You immediately gain that cell's point value

## Winning Conditions

### Primary Win: Three-in-a-Row
Get three of your pieces in a straight line (horizontal, vertical, or diagonal).

**Examples**:
```
Horizontal:          Vertical:           Diagonal:
X . .               X . .               X . .
X . .       OR      . X .       OR      . X .
X . .               . . X               . . X
```

If you get three-in-a-row at any point, **you win immediately** and the game ends.

### Secondary Win: Most Points (If Board Fills)
If all 9 cells are filled without anyone getting three-in-a-row, the player with the most points wins.

**Example**:
```
After 9 moves, board is full:
X beats O with 10 points vs 5 points
```

## Point System

When you place your piece on a cell, you keep that cell's points for the rest of the game:
- Place on **center (3-point cell)**: You get +3 points
- Place on **corner (2-point cell)**: You get +2 points  
- Place on **edge (1-point cell)**: You get +1 point

**Total available**: 2+1+2+1+3+1+2+1+2 = 15 points across all cells

## Game States

| State | How it Ends |
|-------|------------|
| X gets three-in-a-row | X wins immediately |
| O gets three-in-a-row | O wins immediately |
| Board fills, X has more points | X wins by points |
| Board fills, O has more points | O wins by points |

**Note**: A tie is mathematically impossible (15 points cannot be split equally between two players).

## Strategy Tips

- **Control the center**: The center is worth 3 points (most valuable)
- **Block threats**: Blocking an opponent's three-in-a-row also prevents their point gains
- **Corner control**: Corners are worth 2 points (medium value)
- **Plan ahead**: Early moves affect which cells you can claim later
- **Balance**: Balance chasing three-in-a-row with accumulating points

## Playing the Game

1. Open the game in your browser
2. Click cells to place pieces (X goes first)
3. Game displays current scores in real-time
4. First to three-in-a-row wins, OR when board fills, highest points wins
5. Click "New Game" to play again
