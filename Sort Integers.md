# Description

Given an integer array, sort it in ascending order. Use selection sort, bubble sort, insertion sort or any O(n2) algorithm.

# Solution

- quick sort

```
class Solution {
public:
    /*
     * @param A: an integer array
     * @return: 
     */
    void sortIntegers(vector<int> &A) {
        // write your code here
        if (A.empty())
            return;
        qs(A, 0, A.size() - 1);
    }
    void qs(vector<int> &A, int start, int end) {
        if (start >= end) {
            return;
        }
        int left = start, right = end;
        // 1. pivot, not A[start] A[end], get value not index
        int pivot = A[(start + end) / 2];
        // 2. left <= right 最后两个指针错开，之后qs后没有交集
        while (left <=right) {
            // 3. A[left] < pivot
            while (left <= right && A[left] < pivot)
                left++;
            while (left <= right && A[right] > pivot)
                right--;
            if (left <= right) {
                swap(A[left], A[right]);
                left++;
                right--;
            }
        }
        qs(A, start, right);
        qs(A, left, end);
    }
};
```
