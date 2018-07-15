## Word Search

[Description](https://leetcode.com/problems/word-search/description/)

Given a 2D board and a word, find if the word exists in the grid.

The word can be constructed from letters of sequentially adjacent cell, where "adjacent" cells are those horizontally or vertically neighboring. The same letter cell may not be used more than once.

**Example:**

```
board =
[
  ['A','B','C','E'],
  ['S','F','C','S'],
  ['A','D','E','E']
]

Given word = "ABCCED", return true.
Given word = "SEE", return true.
Given word = "ABCB", return false.
```

[Solution]()

Backtracking:


```c++
class Solution {
public:
    bool exist(vector<vector<char>>& board, string word) {
        for (int i = 0; i < board.size(); i++)
            for (int j = 0; j < board[0].size(); j++){
                if (exist_Start(board, word,i, j, 0))
                    return true;
            }
        return false;
    }
private:
    bool exist_Start(vector<vector<char>>& board, string& word, int i, int j, int ind){
        if (i < 0 or i >= board.size() or
            j < 0 or j >= board[0].size() or
            word[ind] != board[i][j]) return false;
        if (word.size() == ind+1) return true;
        //cout << word[0] << ' ' << board[i][j] << endl;
        char tmp = board[i][j];
        board[i][j] = '_';
        bool res = exist_Start(board, word, i-1, j, ind+1) or
                    exist_Start(board, word, i+1, j, ind+1) or
                    exist_Start(board, word, i, j-1, ind+1) or
                    exist_Start(board, word, i, j+1, ind+1);
        board[i][j] = tmp;
        return res;

    }
};
```
