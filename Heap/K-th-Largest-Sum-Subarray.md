# K-th Largest Sum Subarray
#### Problem Statement:
You have been given an **array/list** of `N` integers. Now you are supposed to find the **K-th** largest sum of the _subarray_.
Please note that a _subarray_ is the sequence of consecutive elements of the array.

#### Sample Input 1

2

3 3

3 -2 5

2 2

4 1

#### Sample output 1 :

3

4

#### Explanation of Sample output 1:

**For the first test case,**

Sum of [0, 0] = 3

Sum of [0, 1] = 1

Sum of [0, 2] = 6

Sum of [1, 1] = -2

Sum of [1, 1] = -2

Sum of [1, 2] = 3

Sum of [2, 2] = 5

All sum of subarrays are {6, 5, 3, 3, 1, -2} where the third largest element is 3.

**For the second test case,**

Sum of [0, 0] = 4

Sum of [0, 1] = 5

Sum of [1, 1] = 1

All sum of subarrays are {5, 4, 1} where the second largest element is 4.
