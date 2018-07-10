# Gray Code

[Description](https://leetcode.com/problems/gray-code/description/)
The gray code is a binary numeral system where two successive values differ in only one bit.

Given a non-negative integer n representing the total number of bits in the code, print the sequence of gray code. A gray code sequence must begin with 0.

**Example 1:**

```
Input: 2
Output: [0,1,3,2]
Explanation:
00 - 0
01 - 1
11 - 3
10 - 2

For a given n, a gray code sequence may not be uniquely defined.
For example, [0,2,3,1] is also a valid gray code sequence.

00 - 0
10 - 2
11 - 3
01 - 1
```

**Example 2:**
```
Input: 0
Output: [0]
Explanation: We define the gray code sequence to begin with 0.
             A gray code sequence of n has size = 2n, which for n = 0 the size is 20 = 1.
             Therefore, for n = 0 the gray code sequence is [0].
```

[Solution]()
1) Start with one bit, [0, 1]
2) Asume the first bit is always zero.
3) Always go backward and add 2^1 pushback to the result

```c++
class Solution {
public:
    vector<int> grayCode(int n) {
        if (n == 0) return {0};
        vector<int> res (2, 0);
        res[1] = 1;
        int s = 1, j = 1, i;
        for (int k = 1; k < n; k++){
            i = res.size();
            s *= 2;
            while (i)
                res.push_back(s + res[--i]);
        }
        return res;
        
    }
};
```
