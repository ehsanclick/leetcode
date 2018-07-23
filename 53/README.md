## Maximum Subarray

[Description](https://leetcode.com/problems/maximum-subarray/description/)
Given an integer array nums, find the contiguous subarray (containing at least one number) which has the largest sum and return its sum.

Example:
```
Input: [-2,1,-3,4,-1,2,1,-5,4],
Output: 6
Explanation: [4,-1,2,1] has the largest sum = 6.
```

[Solution]()
Either we add current number to the sum or we start over:

```c++
class Solution {
public:
    int maxSubArray(vector<int>& nums) {
        int ret = INT_MIN, runSum = 0;
        for (auto num:nums){
            runSum = max(runSum+num, num);;
            ret = max (ret, runSum);
        }
        return ret;
    }
};
```
