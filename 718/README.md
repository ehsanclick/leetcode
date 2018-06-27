## Maximum Length of Repeated Subarray

[Description:](https://leetcode.com/problems/maximum-length-of-repeated-subarray/description/)

Given two integer arrays A and B, return the maximum length of an subarray that appears in both arrays.

### Example 1:
`
Input:
A: [1,2,3,2,1]
B: [3,2,1,4,7]
Output: 3
Explanation: 
The repeated subarray with maximum length is [3, 2, 1].
`
Similar to longest common substring[]

[Solution](https://leetcode.com/problems/maximum-length-of-repeated-subarray/discuss/109068/JavaC++-Clean-Code-8-lines)

### Dynamic Programming

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

