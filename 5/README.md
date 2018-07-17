## Longest Palindromic Substring

[Description](https://leetcode.com/problems/longest-palindromic-substring/description/)
Given a string s, find the longest palindromic substring in s. You may assume that the maximum length of s is 1000.

Example 1:
```
Input: "babad"
Output: "bab"
Note: "aba" is also a valid answer.
```
Example 2:
```
Input: "cbbd"
Output: "bb"
```

###Solution:

Expand from the center technique:

In fact, we could solve it in O(n^2) time using only constant space.

We observe that a palindrome mirrors around its center. Therefore, a palindrome can be expanded from its center, and there are only 2n - 12n−1 such centers.

You might be asking why there are 2n - 1 but not n centers? The reason is the center of a palindrome can be in between two letters. Such palindromes have even number of letters (such as "abba") and its center are between the two 'b's.

```c++
class Solution {
public:
    string longestPalindrome(string s) {
        //string ret  =  "";
        int tmp = 0;
        int ind = 0, len = 0;
        for (int i = 0; i < s.size(); i++){
            tmp = max(expand(s, i, i), expand(s, i, i+1));
            if (tmp > len){
                ind = i;
                len = tmp;
            }
        }
        return s.substr(ind - ((len-1)/2), len);
        
    }
private:
    int expand(const string &s, int l, int r){
        while(l>=0 && (r<s.size()) && s[l] == s[r]){
            l--;
            r++;
        }
        return r - l - 1;
    }
};
```

