# 64. Minimum Path Sum
https://leetcode-cn.com/problems/minimum-path-sum  
Given a m x n grid filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.  
Note: You can only move either down or right at any point in time.  

Example 1:    
![image](https://user-images.githubusercontent.com/60777462/153979384-12d12f51-bacc-45eb-bfad-fc6735f93008.png)  
Input: grid = [[1,3,1],[1,5,1],[4,2,1]]  
Output: 7  
Explanation: Because the path 1 → 3 → 1 → 1 → 1 minimizes the sum.  

Example 2:  
Input: grid = [[1,2,3],[4,5,6]]  
Output: 12  

Constraints:  
m == grid.length  
n == grid[i].length  
1 <= m, n <= 200  
0 <= grid[i][j] <= 100  

``` python3
class Solution:
    def minPathSum(self, grid: List[List[int]]) -> int:
        row,col=len(grid),len(grid[0])
        for i in range(1,row):
            grid[i][0]+=grid[i-1][0]
        for j in range(1,col):
            grid[0][j]+=grid[0][j-1]
        for i in range(1,row):
            for j in range(1,col):
                grid[i][j]+=min(grid[i-1][j],grid[i][j-1])
        return grid[-1][-1]
```
