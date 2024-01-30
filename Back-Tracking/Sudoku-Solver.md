# Sudoku Solver

#### Problem Statement:
You have been given a 9x9 2d integer matrix `MAT` representing a Sudoku puzzle. The empty cells of the Sudoku are filled with zeros, and the rest of the cells are filled with integers from 1 to 9. Your task is to fill all the empty cells such that the final matrix represents a Sudoku solution.

#### Note:

**A Sudoku solution must satisfy all the following conditions-**

1. Each of the digits 1-9 must occur exactly once in each row.

2. Each of the digits 1-9 must occur exactly once in each column.

3. Each of the digits 1-9 must occur exactly once in each of the 9, 3x3 sub-grids of the grid.

You can also assume that there will be only one sudoku solution for the given matrix.

#### Input Format:

The input consists of 9 lines. Each line contains 9 single space-separated integers representing a row of the matrix. An empty cell is represented by 0.

#### Constraints:

* `Size of MAT is 9x9`
* `0 <= MAT[i][j] <= 9`

**where an empty cell is given by 0 in the matrix.**

#### Output Format:

The output is consists of 9 lines. Each line contains 9 single space-separated integers where the empty cells from the input matrix are replaced by some integers.

**Code:**

```C++


#include <bits/stdc++.h>
bool isSafe(vector<vector<int>> &sudoku, int row, int col, int val, int n)
{
    for(int i=0;i<n;i++)
    {
        if(sudoku[row][i]==val)
        {
            return false;
        }
        if(sudoku[i][col]==val)
        {
            return false;
        }
        if(sudoku[3*(row/3)+(i/3)][3*(col/3)+(i%3)]==val)
        {
            return false;
        }
    }
    return true;
}
bool solution(vector<vector<int>>& sudoku)
{
    int n = 9;
    for(int row=0; row<n; row++)
    {
        for(int col=0; col<n; col++)
        {
            if(sudoku[row][col]==0)
            {
                for(int val=1;val<=9;val++)
                {
                    if(isSafe(sudoku, row, col, val, n))
                    {
                        sudoku[row][col]=val;
                        bool next = solution(sudoku);
                        if(next)
                        {
                            return true;
                        }
                        else
                        {
                            sudoku[row][col]=0;
                        }
                    }
                }
                return false;
            }
        }
    }
    return true;
}
void solveSudoku(vector<vector<int>>& sudoku)
{
    // Write your code here
    // No need to print the final sudoku
    // Just fill the values in the given matrix
    bool ans = solution(sudoku);
}


```
