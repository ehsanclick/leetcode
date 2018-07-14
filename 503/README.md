## Next Greater Element

[Description](https://leetcode.com/problems/next-greater-element-ii/)

Given a circular array (the next element of the last element is the first element of the array), print the Next Greater Number for every element. The Next Greater Number of a number x is the first greater number to its traversing-order next in the array, which means you could search circularly to find its next greater number. If it doesn't exist, output -1 for this number.

**Example 1:**
```
Input: [1,2,1]
Output: [2,-1,2]
Explanation: The first 1's next greater number is 2; 
The number 2 can't find next greater number; 
The second 1's next greater number needs to search circularly, which is also 2.
```

[Solution]
Normal array (No circular)

Use stack to store in irder largest elements from the end.
With circular array, use twice the size!

```c++
class Solution {
public:
    vector<int> nextGreaterElements(vector<int>& nums) {
        if (!nums.size()) return {}; 
        std::stack<int> g;
        vector<int> res (nums.size(), -1);
        for (int i = 2 * nums.size() - 1; i >= 0; i--){
            while (!g.empty() and g.top() <= nums[i % nums.size()])
                g.pop();
            if (!g.empty() and g.top() >= nums[i % nums.size()])
                res[i%nums.size()] = g.top();
            g.push(nums[i%nums.size()]);
        }
        return res;        
    }
};
```

