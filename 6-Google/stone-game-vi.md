# Stone Game VI

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/stone-game-vi/description/)

Alice and Bob take turns playing a game, with Alice starting first.

There are n stones in a pile. On each player's turn, they can remove a stone from the pile and 
receive points based on the stone's value. Alice and Bob may value the stones differently.

You are given two integer arrays of length n, aliceValues and bobValues. Each aliceValues[i] and bobValues[i] 
represents how Alice and Bob, respectively, value the ith stone.

The winner is the person with the most points after all the stones are chosen. If both players have the same 
amount of points, the game results in a draw. Both players will play optimally.
Both players know the other's values.

Determine the result of the game, and:
- If Alice wins, return 1.
- If Bob wins, return -1.
- If the game results in a draw, return 0.

### Sample Input
```
aliceValues = [1,3], bobValues = [2,1]
```

### Sample Output
```
1

Explanation:
If Alice takes stone 1 (0-indexed) first, Alice will receive 3 points.
Bob can only choose stone 0, and will only receive 2 points.
Alice wins.
```

### Solution
```cpp
class Solution {
public:
    int stoneGameVI(vector<int>& aliceValues, vector<int>& bobValues) {
        vector<pair<int, int>> pairs;

        for (int i = 0; i < aliceValues.size(); i++) {
            pairs.push_back({aliceValues[i], bobValues[i]});
        }
        sort(pairs.begin(), pairs.end(), [](const auto& a, const auto& b) {
            return (a.first + a.second) > (b.first + b.second);
        });

        int aliceTotal = 0, bobTotal = 0;

        for (int i = 0; i < pairs.size(); i++) {
            if (i % 2 == 0) {
                aliceTotal += pairs[i].first;
            } else {
                bobTotal += pairs[i].second;
            }
        }
        
        if (aliceTotal > bobTotal) {
            return 1;
        } else if (bobTotal > aliceTotal) {
            return -1;
        } else {
            return 0;
        }
    }
};
```
