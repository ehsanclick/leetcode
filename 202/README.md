# Happy Number

[Description](https://leetcode.com/problems/happy-number/description/)

Write an algorithm to determine if a number is "happy".

A happy number is a number defined by the following process: Starting with any positive integer, replace the number by the sum of the squares of its digits, and repeat the process until the number equals 1 (where it will stay), or it loops endlessly in a cycle which does not include 1. Those numbers for which this process ends in 1 are happy numbers.
```
Example: 

Input: 19
Output: true
Explanation: 
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

[Solution]()

**Fast / Slow pointer **
Similar to linked list cycle, etc.

```c++
class Solution {
public:
    bool isHappy(int n) {
        int i = n; // i slow pointer, n fast
        do{
            n = digSum(n);
            n = digSum(n);
            i = digSum(i);
        }while(n != i);
        if (i == 1) return true;
        return false;
    }
private:
    int digSum(int n) {
        int dSum = 0, dig;
        while (n){
            dig = n % 10;
            dSum += dig * dig;
            n /= 10;
        }
        return dSum;
    }
};
```

