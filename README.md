# N-Queen Visualizer

This is a React simulation of the backtracking algorithm used to solve the N-Queen problem.

### Background

The n-queens puzzle is the problem of placing _n_ chess queens on an _nxn_ chessboard such that no two queens threaten each other; thus, a solution requires that no two queens share the same row, column, or diagonal. 

Solutions exist for all natural numbers _n_ with the exception of _n=2_ and _n=3_. Although the exact number of solutions is only known for <em>n<=27</em>, the asymptotic growth rate of the number of solutions is approximately <em>0.143n</em><sup>n</sup>.

_[Source](https://en.wikipedia.org/wiki/Eight_queens_puzzle_)_

### Notes on Algorithm Design

The backtracing algorithm for solving the n-queen problem is as follows:
1. Initialize an empty chessboard of size nxn
2. Place a queen in the first row of the leftmost column of the board
3. Move to the next column and place a queen in the first row of said column
4. Repeat _step 3_ until either:
	1. all N queens have been placed OR 
	2. it is impossible to place a queen in the current column without violating the rules of the problem. 
5. If all n queens have been placed, print/ display the solution.
6. If it is not possible to place a queen in the current column without violating the rules of the problem, backtrack to the previous column.
7. Remove the queen from the previous column and nmove it down one row.
8. Repeat steps _4 through 7_ until all possible configurations have been tried.

##### Psuedocode implementation

_Recursive utility driver function_

``` 
	function solveNQueens(board, col, n):
		if col >= n:
			print board
	 		return true
		for row = 0 to row = n-1:
			if isSafe(board, row, col, n):
	 			board[row][col] = 1
 			if solveNQueens(board, col+1, n):
				return true

			board[row][col] = 0
		return false
```

_Utility function used to check if a queen can be placed in cell board[row][col]_

``` 
	function isSafe(board, row, col, n):
		for i = 0 to i = col-1:
			if board[row][i] == 1:
				return false
		for i = row, j = col; i >= 0 && j >= 0; i--, j--:
			if board[i][j] == 1:
				return false
 		for i = row, j = col; j >= 0 && i < n; i++, j--:
			if board[i][j] == 1
				return false
		return true
```

_Initialization_

``` 
	board = empty nxn matrix
	solveNQueens(board, 0, n)
```

_[Reference](https://www.geeksforgeeks.org/n-queen-problem-backtracking-3/)_

### Demo

To start, clone the repo and run _npm start_.

Alternately, a live project demo is hosted [here.](https://camilamdaniels.github.io/queens-gambit/.)


