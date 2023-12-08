# Minimum Cost of ropes
#### Problem Statement:
There are given `N` ropes of different lengths, we need to connect these ropes into one rope. The cost to connect two ropes is equal to sum of their lengths. 
The task is to connect the ropes with minimum cost. Given `N` size array `arr[]` contains the lengths of the ropes.

#### Example 1:

**Input:**
n = 4

arr[] = {4, 3, 2, 6}

**Output:** 29

#### Explanation:

**We can connect the ropes in following ways.**

1) First connect ropes of lengths 2 and 3. Which makes the array {4, 5, 6}. Cost of this operation 2+3 = 5.
2) Now connect ropes of lengths 4 and 5. Which makes the array {9, 6}. Cost of this operation 4+5 = 9.
3) Finally connect the two ropes and all ropes have connected. Cost of this operation 9+6 =15

Total cost for connecting all ropes is 5 + 9 + 15 = 29. This is the optimized cost for connecting ropes.
Other ways of connecting ropes would always have same or more cost. For example, if we connect 4 and 6 first (we get three rope of 3, 2 and 10), then connect 10 and 3 (we get two rope of 13 and 2). 
Finally we connect 13 and 2. Total cost in this way is 10+ 13 + 15 = 38.

#### Code:

```C++
//{ Driver Code Starts
#include <bits/stdc++.h>
using namespace std;


// } Driver Code Ends
class Solution
{
    public:
    //Function to return the minimum cost of connecting the ropes.
    long long solution(priority_queue<long long, vector<long long>, greater<long long>> &q, long long &sum)
    {
        if(q.size()==1)
        {
            return 0;
        }
        
        while(q.size()!=1 && q.size()!=0)
        {
            long long num1 = q.top();
        
            if(!q.empty())
                q.pop();
                
            long long num2 = q.top();
            
            if(!q.empty())
                q.pop();
                
            long long count = num1 + num2;
            q.push(count);
            
            sum += count ;
            
        }
        
        return sum;
    }
    
    long long minCost(long long arr[], long long n) {
        // Your code here
        priority_queue<long long, vector<long long>, greater<long long>> q;
        long long sum = 0;
        for(long long i=0;i<n;i++)
        {
            q.push(arr[i]);
        }
        
        long long ans = solution(q, sum);
        return ans;
        
    }
};


//{ Driver Code Starts.

int main() {
    long long t;
    cin >> t;
    while (t--) {
        long long n;
        cin >> n;
        long long i, a[n];
        for (i = 0; i < n; i++) {
            cin >> a[i];
        }
        Solution ob;
        cout << ob.minCost(a, n) << endl;
    }
    return 0;
}

// } Driver Code Ends

```
