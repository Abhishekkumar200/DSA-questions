# N Queens

#### Problem Statement:
You are given an integer `N`. For a given `N` x `N` chessboard, find a way to place `N` **queens** such that no **queen** can attack any other **queen** on the chessboard.
A **queen** can be killed when it lies in the same _row_, or same _column_, or the same _diagonal_ of any of the other **queens**. You have to print all such configurations.

#### Constraints:
* `1<= N <= 10`
* `Time limit: 1sec`

#### Sample Input 1:

4

#### Sample Output 1:

0010100000010100

0100000110000010

#### Explanation For Sample Input 1:

Output depicts two possible

Output depicts two possible configurations of the chessboard for 4 queens.

The Chessboard matrix for the first configuration looks as follows:-

0010

1000

0001

0100

Queen contained cell is depicted by 1. As seen, No queen is in the same row, column, or diagonal as the other queens. Hence this is a valid configuration.

#### Code:

```C++

void pushAns(vector<vector<int>> &arr, vector<vector<int>> &ans, int n)
{
    vector<int> temp;
    for(int i=0;i<n;i++)
    {
        for(int j=0;j<n;j++)
        {
            // cout<<arr[i][j]<<" ";
            temp.push_back(arr[j][i]);
        }
        // cout<<endl;
    }
    
    ans.push_back(temp);
}
bool isSafe(vector<vector<int>> &arr, int column, int row, int n)
{
    int r = row;
    int c = column;
    while(r>=0 && c>=0)
    {
        if(arr[r][c]==1)
        {
            return false;
        }
        r--;
        c--;
    }
    c = column;
    r = row;
    while(c>=0 && r>=0)
    {
        if(arr[r][c]==1)
        {
            return false;
        }
        c--;
    }
    c = column;
    r = row;
    while(c>=0 && r>=0 && r<n && c<n)
    {
        if(arr[r][c]==1)
        {
            return false;
        }
        c--;
        r++;
    }
    return true;
}
void solve(vector<vector<int>> &arr, vector<vector<int>> &ans, int n, int column)
{
    if(column==n)
    {
        pushAns(arr, ans, n);
        return;
    }
    for(int row=0;row<n;row++)
    {
        if(isSafe(arr, column, row, n))
        {
            arr[row][column] = 1;
            solve(arr, ans, n, column+1);
            arr[row][column] = 0;
        }
    }
}
vector<vector<int>> solveNQueens(int n) {
    // Write your code here.
    vector<vector<int>> arr(n, vector<int>(n, 0));
    vector<vector<int>> ans;
    solve(arr, ans, n, 0);
    return ans;
}

```


