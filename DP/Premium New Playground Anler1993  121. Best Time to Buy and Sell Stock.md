双重循环  时间超时
```
class Solution:
    def maxProfit(self, prices):
        """
        :type prices: List[int]
        :rtype: int
        """
        res = 0

        for i in range(len(prices)):
            for j in range(i,len(prices)):
                res= max(res,prices[j]-prices[i])

        return res
```
