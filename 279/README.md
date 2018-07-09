# Perfect Squares
[Description](https://leetcode.com/problems/perfect-squares/description/)
Given a positive integer n, find the least number of perfect square numbers (for example, 1, 4, 9, 16, ...) which sum to n.

**Example 1:**
```
Input: n = 12
Output: 3 
Explanation: 12 = 4 + 4 + 4.
```

**Example 2:**
```
Input: n = 13
Output: 2
Explanation: 13 = 4 + 9.
```

[Solution](https://leetcode.com/problems/perfect-squares/discuss/71488/Summary-of-4-different-solutions-(BFS-DP-static-DP-and-mathematics))
**Dynamic Programming**

1) Create an array of all squeares less than n
2) Create an array of least number of perfect square numbers of numbers upp to n;
 - for each --i-- check the posible number by choosing each sq number less than --i--

```c++
class Solution {
public:
    int numSquares(int n) {
        vector<int> psq;
        int i = 1;
        int j = 1;
        while(j <= n){
            psq.push_back(j);
            i++;
            j = i*i;
        }
        vector<int> nsq(n+1, INT_MAX);
        nsq[0] = 0;
        for (i = 1; i <= n; i++){
            j = 0;
            while(j < psq.size() && psq[j] <= i)
                nsq[i] = min (nsq[i], nsq[i - psq[j++]]+1);
        }
        return nsq[n];
    }
};
```

