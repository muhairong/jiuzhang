# Description

Given an integer array, sort it in ascending order. Use quick sort, merge sort, heap sort or any O(nlogn) algorithm.

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
- merge sort
    - using extra O(n) space to merge
```
class Solution {
public:
    /*
     * @param A: an integer array
     * @return: 
     */
    void sortIntegers2(vector<int>& A) {
        // write your code here
        if (A.size() <= 1)
            return;
        vector<int> tmp(A.size(), 0);
        mergesort(A, 0, A.size() - 1, tmp);
    }
    void mergesort(vector<int> &A, int start, int end, vector<int> &tmp) {
        if (start >= end)
            return;
        mergesort(A, start, (start + end) / 2, tmp);
        mergesort(A, (start + end) / 2 + 1, end, tmp);
        merge(A, start, end, tmp);
    }
    void merge(vector<int> &A, int start, int end, vector<int> &tmp) {
        int mid = (start + end) / 2;
        int lindex = start, rindex = mid + 1, index = start;
        while (lindex <= mid && rindex <= end) {
            if (A[lindex] < A[rindex])
                tmp[index++] = A[lindex++];
            else
                tmp[index++] = A[rindex++];
        }
        while (lindex <= mid)
            tmp[index++] = A[lindex++];
        while (rindex <= end)
            tmp[index++] = A[rindex++];
        for (int i = start; i <= end; ++i)
            A[i] = tmp[i];
    }
};
```
