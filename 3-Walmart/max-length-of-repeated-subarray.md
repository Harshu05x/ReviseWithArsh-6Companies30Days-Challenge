# Maximum Length of Repeated Subarray

[![Problem Link](https://img.shields.io/badge/-LeetCode-FFA116?style=for-the-badge&logo=LeetCode&logoColor=black)](https://leetcode.com/problems/maximum-length-of-repeated-subarray/description/)

Given two integer arrays `nums1` and `nums2`, return the maximum length of a `subarray` that appears in both arrays.

### Sample Input
```
nums1 = [1,2,3,2,1], nums2 = [3,2,1,4,7]
```

### Sample Output
```
3

Explanation: The repeated subarray with maximum length is [3,2,1].
```

### Solution
```cpp
class Solution {
public:
    int findLength(vector<int>& nums1, vector<int>& nums2) {
        
        int m = nums1.size();
        int n = nums2.size();
        vector<vector<int>> dp(m+1,vector<int>(n+1,0));

        int ans = 0;
        for(int i = 1; i <= m; i++){
            for(int j = 1; j <= n; j++){
                if(nums1[i-1] == nums2[j-1]){
                    dp[i][j] = 1 + dp[i-1][j-1];
                    ans = max(ans,dp[i][j]);
                }
            }
        }
        return ans;
    }
};
```
