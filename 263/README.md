#Ugly Number

**EASY ONE**

[Description](https://leetcode.com/problems/ugly-number/description/)

Write a program to check whether a given number is an ugly number.

Ugly numbers are positive numbers whose prime factors only include 2, 3, 5.

**Example 1:**
```
Input: 6
Output: true
Explanation: 6 = 2 × 3
```
**Example 2:**
```
Input: 8
Output: true
Explanation: 8 = 2 × 2 × 2
```
**Example 3:**
```
Input: 14
Output: false 
Explanation: 14 is not ugly since it includes another prime factor 7.
```

[Solution](https://leetcode.com/problems/ugly-number/discuss/69214/2-4-lines-every-language)

Just divide by 2, 3 and 5 as often as possible and then check whether we arrived at 1. Also try divisor 4 if that makes the code simpler / less repetitive.
Just check all factors <=5. (4 = 2 x 2 so 4 is ok and increases the speed )

```c++
class Solution {
public:
    bool isUgly(int num) {
        if (num <= 0) return false;
        for (int i = 5; i > 1; i--)
            while (num % i == 0)
                num /= i;
        return (num == 1);
    }
};
```
