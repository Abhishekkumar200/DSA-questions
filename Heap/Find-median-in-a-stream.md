# Find median in a stream

#### Problem Statement:

Given an input stream of `N` integers. The task is to insert these numbers into a new stream and find the *median* of the stream formed by each insertion of `X` to the new stream.

#### Example 1:

**Input:**

N = 4

X[] = {5,15,1,3}

**Output:**

5

10

5

4

**Explanation:** Flow in stream: {5, 15, 1, 3}

5 goes to stream --> _median_ 5 (5)

15 goes to stream --> _median_ 10 (5,15)

1 goes to stream --> _median_ 5 (5,15,1)

3 goes to stream --> _median_ 4 (5,15,1 3)

#### Your Task:

You are required to complete the class `Solution`. It should have 2 data members to represent 2 **heaps**.

**It should have the following member functions:**

1. `insertHeap()` which takes `x` as input and inserts it into the **heap**, the function should then call `balanceHeaps()` to balance the new **heap**.

2. `balanceHeaps()` does not take any arguments. It is supposed to balance the two **heaps**.

3. `getMedian()` does not take any arguments. It should return the current _median_ of the stream.

**Expected Time Complexity:** O(nlogn)

**Expected Auxilliary Space:** O(n)

#### Constraints:

* `1 <= N <= 106`

* `1 <= x <= 106`

#### Code:

```C++

class Solution
{
    public:
    
    priority_queue<int, vector<int>, greater<int>> minHeap;
    priority_queue<int> maxHeap;

    //Function to insert heap.
    void insertHeap(int &x)
    {
        if(maxHeap.empty())
        {
            maxHeap.push(x);
            return;
        }
        
        if(maxHeap.size()>minHeap.size())
        {
            if(x>maxHeap.top())
            {
                minHeap.push(x);
            }
            else
            {
                minHeap.push(maxHeap.top());
                maxHeap.pop();
                maxHeap.push(x);
            }
        }
        else
        {
            if(x>maxHeap.top())
            {
                minHeap.push(x);
                maxHeap.push(minHeap.top());
                minHeap.pop();
            }
            else
            {
                maxHeap.push(x);
            }
        }
    }
    
    //Function to balance heaps.
    void balanceHeaps()
    {
        return;
    }
    
    //Function to return Median.
    double getMedian()
    {
        if(maxHeap.size()==minHeap.size())
        {
            return (double)(maxHeap.top()+minHeap.top())/2.0;
        }
        else 
        {
            return maxHeap.top();
        }
    }
};

```
