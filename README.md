# Raichu - A Game Playing AI Agent

### Pieces in the game

#### 1] A Pichu:
- Moves one square forward diagonally, if that square is empty. 
- Jumps over a single Pichu of the opposite color by moving two squares forward diagonally if that square is empty. The jumped piece of opponent team is removed from the board as soon as it is jumped. 

#### 2] A Pikachu:
- Moves 1 or 2 squares either forward, left, or right (but not diagonally) to an empty square, as long as all squares in between are also empty.
- Jumps over a single Pichu/Pikachu of the opposite color by moving 2 or 3 squares forward, left, or right (not diagonally), as long as all of the squares between the Pikachu’s start position and jumped piece are empty and all the squares between the jumped piece and the ending position are empty. The jumped piece of opponent player is removed as soon as it is jumped. 

#### 3] A Raichu: created when a Pichu or Pikachu reaches the opposite side of the board 
- Moves any number of squares forward/backward, left, right or diagonally, to an empty square, as long as all squares in between are also empty. 
- Jumps over a single Pichu/Pikachu/Raichu of the opposite color and landing any number of squares forward/backward, left, right or diagonally, as long as all of the squares between the Raichu’s start position and jumped piece are empty and all the squares between the jumped piece and the ending position are empty. The jumped piece of opponent player is removed as soon as it is jumped. 


## State Abstraction:
### Set of Valid States: 
All possible permutation of boards which contains pichu, pikachu and raichu of both players – white as well as black.

### Initial state:
Initial state will be a valid board which contains pichu, pikachu and raichu of both players – white as well as black and passed as command line argument

### Successor function:
Takes a board as input and returns a set of valid boards where either for Player – white or black:
Successor function considers that 
*Pichus can only capture Pichus, Pikachus can capture Pichus or Pikachus, while Raichus can capture any piece of opponent player**

### Heuristic Function

I have used 3 heuristics for computing the optimal (best) successor for any given board.

#### 1] Heuristic 1:
- This computes the aggregate of the weighted difference in the number pichus, pikachus and raichus respectively for both players.
- For any given player, maximizing this heuristic would increase their chances of winning.

#### 2] Heuristic 2:
- This computes the value which is inversely related to the distance for any piece (pichu or pikachu) to reach the opposite side. The lesser the distance, the greater is this value which increases the likelihood of selecting a successor. 

#### 3] Heuristic 3:
- This computes the number of boxes(positions) that a given piece can control from its position. This indicates the number of moves that piece can make. 


### Goal State:
A board where one player captures all the pieces of opponent player


### Approach:

- For this program, I have used minimax algorithm with alpha-beta pruning up to height = 2
- So, for any given board, the program will take 2 levels of successors into consideration. Here, the max-player will select the maximum value from beta values returned by its successors, and the min-player will select the minimum value from alpha values returned by its successor.
- Likewise, each player at any given state will try to maximize its chances of winning.

*The output that I am getting takes an average time of 5~6 secs for height 2. I also tried running the algorithm for height 3 and height 4, which gave better results but took a longer time of ~9.76secs and ~80secs respectively.*

![Screen Shot 2021-11-05 at 10 44 58 PM](https://media.github.iu.edu/user/18454/files/81c61600-3e93-11ec-80cf-ae5fdf4cc061)








