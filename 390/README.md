## Elimination Game

[Description](https://leetcode.com/problems/elimination-game/description/)

There is a list of sorted integers from 1 to n. Starting from left to right, remove the first number and every other number afterward until you reach the end of the list.

Repeat the previous step again, but this time from right to left, remove the right most number and every other number from the remaining numbers.

We keep repeating the steps again, alternating left to right and right to left, until a single number remains.

Find the last number that remains starting with a list of length n.

**Example:**
```
Input:
n = 9,
1 2 3 4 5 6 7 8 9
2 4 6 8
2 6
6

Output:
6
```

[Solution](https://leetcode.com/problems/elimination-game/discuss/87121/O(logN)-solution.-clear-break-down)

**Recursion:**

The next round is always even. All odds eliminates on first round
Next round is a new sequence if we devide by two.
Every round is a new sequence of previous round if we devide by two.
On left two right we always start from 1 (odd numbers eliminate)
On right to left it depends on the number of n:
 - if _*n*_ is odd: start from begining (odd number eliminate)
 - if _*n*_ is even: start from 2 (even numbers eliminate) 

```c++
class Solution {
public:
    int lastRemaining(int n) {
      return leftToRight(n);
    }

private:
    static int leftToRight(int n) {
      if(n <= 2) return n;
      return 2 * rightToLeft(n / 2);
    }

    static int rightToLeft(int n) {
      if(n <= 2) return 1;
      if(n % 2 == 1) return 2 * leftToRight(n / 2);
      return 2 * leftToRight(n / 2) - 1;
    }
};
```
