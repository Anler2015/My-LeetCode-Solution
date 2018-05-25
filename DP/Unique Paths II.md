```
class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid):
        """
        :type obstacleGrid: List[List[int]]
        :rtype: int
        """
        row = len(obstacleGrid)
        col = len(obstacleGrid[0])
        #dp代表到这个点的路径数
        dp = [[0 for i in range(col)] for row in range(row)]
        
        #初始化状态
        for i in range(row):
            if obstacleGrid[i][0] == 0:
                dp[i][0] =1
            else:
                break

        for i in range(col):
            if obstacleGrid[0][i] ==0:
                dp[0][i] =1
            else:
                break

        #状态方程
        for i in range(1,row):
            for j in range(1,col):
                dp[i][j] = dp[i-1][j]+dp[i][j-1]
                if obstacleGrid[i][j] == 1:
                    dp[i][j] = 0

        return dp[row-1][col-1]
```
