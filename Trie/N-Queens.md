# N Queens

#### Problem Statement:
You are given an integer `N`. For a given `N` x `N` chessboard, find a way to place `N` **queens** such that no **queen** can attack any other **queen** on the chessboard.
A **queen** can be killed when it lies in the same row, or same column, or the same diagonal of any of the other **queens**. You have to print all such configurations.

#### Constraints:
* `1<= N <= 10`
* `Time limit: 1sec`
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


