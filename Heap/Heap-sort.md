# Heap Sort

### Problem Statement:
Implement Heap sort.

### Code:

```C++

#include<iostream>
using namespace std;

void heapify(int arr[], int n, int i)
{
    int largest = i;
    int left = 2*i;
    int right = 2*i + 1;
    if(left<=n && arr[left]<arr[largest])
    {
        largest = left;
    }
    if(right<=n && arr[right]<arr[largest])
    {
        largest = right;
    }
    if(largest != i)
    {
        swap(arr[i], arr[largest]);
        heapify(arr, n, largest);
    }
}

void buildHeap(int arr[], int n)
{
    for(int i=n/2;i>0;i--)
    {
        heapify(arr, n, i);
    }
}

void heapSorting(int arr[], int n)
{
    int size = n;
    while(size>1)
    {
        swap(arr[1], arr[size]);
        size--;
        heapify(arr, size, 1);
    }
}

void print(int arr[], int n)
{
    for(int i=1; i<=n; i++)
    {
        cout<<arr[i]<<" ";
    }
    cout<<endl;
}

int main()
{
    int arr[7] = {-1, 9, 3, 8, 5, 4, 2};
    int n = 6;
    buildHeap(arr, n);
    print(arr, n);
    heapSorting(arr, n);
    print(arr, n);
    return 0;
}

```
