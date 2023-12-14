# Smallest Range Covering Elements from K Lists

#### Problem Statement:
You have `k` lists of sorted integers in **non-decreasing order**. Find the **smallest** range that includes at least one number from each of the k lists.

We define the range `[a, b]` is smaller than range `[c, d]` if `b - a < d - c` or `a < c` if `b - a == d - c`.

#### Example 1:

**Input:** nums = [[4,10,15,24,26], [0,9,12,20], [5,18,22,30]]

**Output:** [20,24]

#### Explanation:

*List 1:* [4, 10, 15, 24, 26], 24 is in range [20,24].

*List 2:* [0, 9, 12, 20], 20 is in range [20,24].

*List 3:* [5, 18, 22, 30], 22 is in range [20,24].

#### Example 2:

**Input:** nums = [[1,2,3], [1,2,3], [1,2,3]]

**Output:** [1,1]

#### Constraints:

* `nums.length == k`

* `1 <= k <= 3500`

* `1 <= nums[i].length <= 50`

* `-10^5 <= nums[i][j] <= 10^5`

* `nums [i] is sorted in non-decreasing order`.

#### Code:

```C++

class node
{
    public:
    int data;
    int row;
    int column;
    node(int data, int row , int column)
    {
        this->data = data;
        this->row = row;
        this->column = column;
    }
};

class comp
{
    public:
    bool operator()(node *a, node *b)
    {
        return a->data>b->data;
    }
};

class Solution {
public:
    vector<int> smallestRange(vector<vector<int>>& nums) {
        
        priority_queue<node*, vector<node*>, comp> minHeap;
        vector<int> ans;
        int maxi = INT_MIN;
        int mini = INT_MAX;
        int k = nums.size();
        for(int i=0;i<k;i++)
        {
            node *temp = new node(nums[i][0], i, 0);
            minHeap.push(temp);
            maxi = max(maxi, nums[i][0]);
            mini = min(mini, nums[i][0]);
        }
        int start = mini;
        int end = maxi;
        while(!minHeap.empty())
        {
            node *tmp = minHeap.top();
            minHeap.pop();
            mini = tmp->data;
            if(maxi-mini<end-start)
            {
                start = mini;
                end = maxi;
            }
            int row = tmp->row;
            int column = tmp->column;
            int rowSize = nums[row].size();
            
            if(column+1 < rowSize)
            {
                maxi = max(maxi, nums[row][column+1]);
                minHeap.push(new node(nums[row][column+1], row, column+1));
            }
            else
            {
                break;
            }
        }
        ans.push_back(start);
        ans.push_back(end);
        return ans;
    }
}

```
