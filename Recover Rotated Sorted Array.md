# Description

Given a rotated sorted array, recover it to sorted array in-place.

# Solution

- 3-step reverse
```
class Solution {
public:
    /*
     * @param nums: An integer array
     * @return: nothing
     */
    void recoverRotatedSortedArray(vector<int> &nums) {
        // write your code here
        if (nums.size() <= 1)
            return;
        int index;
        for (index = 0; index < nums.size() - 1; ++index) {
            if (nums[index] > nums[index + 1])
                break;
        }
        if (index == nums.size() - 1)
            return;
        else {
            reverse(nums, 0, index);
            reverse(nums, index + 1, nums.size() - 1);
            reverse(nums, 0, nums.size() - 1);
        }
    }
    void reverse(vector<int> &nums, int l, int r) {
        while (l < r) {
            swap(nums[l], nums[r]);
            l++;
            r--;
        }
    }
};
```
