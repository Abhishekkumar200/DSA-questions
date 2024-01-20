# Sudoku Solver

#### Problem Statement:
You have been given a 9x9 2d integer matrix 'MAT' representing a Sudoku puzzle. The empty cells of the Sudoku are filled with zeros, and the rest of the cells are filled with integers from 1 to 9. Your task is to fill all the empty cells such that the final matrix represents a Sudoku solution.

#### Note:

A Sudoku solution must satisfy all the following conditions-

1. Each of the digits 1-9 must occur exactly once in each row.

2. Each of the digits 1-9 must occur exactly once in each column.

3. Each of the digits 1-9 must occur exactly once in each of the 9, 3x3 sub-grids of the grid.

You can also assume that there will be only one sudoku solution for the given matrix.

#### Input Format:

The input consists of 9 lines. Each line contains 9 single space-separated integers representing a row of the matrix. An empty cell is represented by 0.

#### Constraints:

Size of MAT is 9x9

0 <= MAT[i][j] <= 9

where an empty cell is given by 0 in the matrix.
