## Maximum Length of Repeated Subarray

[Description:](https://leetcode.com/problems/maximum-length-of-repeated-subarray/description/)

Given two integer arrays A and B, return the maximum length of an subarray that appears in both arrays.

### Example 1:
```
Input:
A: [1,2,3,2,1]
B: [3,2,1,4,7]
Output: 3
Explanation: 
The repeated subarray with maximum length is [3, 2, 1].
```
Similar to longest common substring[]

[Solution](https://leetcode.com/problems/maximum-length-of-repeated-subarray/solution/)

### Dynamic Programming
Since a common subarray of A and B must start at some `A[i]` and `B[j]`, let `dp[i][j]` be the longest common prefix of `A[i:]` and `B[j:]`. Whenever `A[i]` == `B[j]`, we know `dp[i][j] = dp[i+1][j+1] + 1`. Also, the answer is `max(dp[i][j])` over all _i, j_.

We can perform bottom-up dynamic programming to find the answer based on this recurrence. Our loop invariant is that the answer is already calculated correctly and stored in dp for any larger _i, j_.

**Complexity Analysis**

 - Time Complexity: O(M∗N), where M,N are the lengths of A, B.
 - Space Complexity: O(M∗N), the space used by dp.


[Optimization](https://leetcode.com/problems/maximum-length-of-repeated-subarray/discuss/109068/JavaC++-Clean-Code-8-lines)
We can optimize the memory to O(min(M,N).
We start with length 1. In code bellow, starting _i_ from end of A means starting with length of 1. _j_ starts from begining and look at the dp[j+1] from previuse iteration (length or _i_)


```cpp
int findLength(vector<int>& A, vector<int>& B) {
    int aSize = A.size(), bSize = B.size();
    if (!aSize | !bSize) return 0;
    vector<int> dp (bSize + 1, 0);
    int res = 0;
    for (int i = aSize - 1; i >= 0; i--)
        for (int j = 0; j < bSize; j++)
            res = max(res, dp[j] = A[i] == B[j] ? dp[j+1]+1 : 0);
    return res;
}
'''

