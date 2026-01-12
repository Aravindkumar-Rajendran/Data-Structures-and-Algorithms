# Valid Sudoku

You are given a 9 x 9 Sudoku board board. A Sudoku board is valid if the following rules are followed:

Each row must contain the digits 1-9 without duplicates.  
Each column must contain the digits 1-9 without duplicates.  
Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without duplicates.  
Return true if the Sudoku board is valid, otherwise return false  

Note: A board does not need to be full or be solvable to be valid.

### Example 1:
![sudoku_image](./sudoku_image.png)


Input: board =   
[["1","2",".",".","3",".",".",".","."],  
 ["4",".",".","5",".",".",".",".","."],  
 [".","9","8",".",".",".",".",".","3"],  
 ["5",".",".",".","6",".",".",".","4"],  
 [".",".",".","8",".","3",".",".","5"],  
 ["7",".",".",".","2",".",".",".","6"],  
 [".",".",".",".",".",".","2",".","."],  
 [".",".",".","4","1","9",".",".","8"],  
 [".",".",".",".","8",".",".","7","9"]]

Output: true

### Example 2:

Input: board =  
[["1","2",".",".","3",".",".",".","."],  
 ["4",".",".","5",".",".",".",".","."],  
 [".","9","1",".",".",".",".",".","3"],  
 ["5",".",".",".","6",".",".",".","4"],  
 [".",".",".","8",".","3",".",".","5"],  
 ["7",".",".",".","2",".",".",".","6"],  
 [".",".",".",".",".",".","2",".","."],  
 [".",".",".","4","1","9",".",".","8"],  
 [".",".",".",".","8",".",".","7","9"]]

Output: false

Explanation: There are two 1's in the top-left 3x3 sub-box.

### Constraints:

board.length == 9  
board[i].length == 9  
board[i][j] is a digit 1-9 or '.'  

### Solution

```python
def isValidSudoku(self, board: List[List[str]]) -> bool:
    for i in range(9):
        # rows check
        row = [r for r in board[i] if r != '.']
        if len(row)!=len(set(row)):
            return False

        # columns check
        col = []
        for row in board:
            if row[i] != '.':
                col.append(row[i])

        if len(col) != len(set(col)):
            return False

    # square check
    for c in range(3):
        for r in range(3):
            square = []
            for b1 in range(c*3, c*3+3):
                for b2 in range(r*3, r*3+3):
                    if board[b1][b2] != ".":
                        square.append(board[b1][b2])
            if len(square) != len(set(square)):
                return False
                
    return True
    
```