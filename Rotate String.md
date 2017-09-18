# Description

Given a string and an offset, rotate string by offset. (rotate from left to right)

# Solution

- 3-step reverse
```
class Solution {
public:
    /*
     * @param str: An array of char
     * @param offset: An integer
     * @return: nothing
     */
    void rotateString(string &str, int offset) {
        // write your code here
        if (str.size() <= 1)
            return;
        offset = offset % str.size();
        reverse(str, 0, str.size() - offset - 1);
        reverse(str, str.size() - offset, str.size() - 1);
        reverse(str, 0, str.size() - 1);
    }
    void reverse(string &str, int l, int r) {
        while (l < r) {
            swap(str[l], str[r]);
            l++;
            r--;
        }
    }
};
```
