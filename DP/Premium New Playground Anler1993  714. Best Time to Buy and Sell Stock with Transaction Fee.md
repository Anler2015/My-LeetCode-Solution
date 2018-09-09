```
class Solution:
    def maxProfit(self, prices, fee):
        """
        :type prices: List[int]
        :type fee: int
        :rtype: int
        """
        if not prices or len(prices) <= 1:
            return 0

        size = len(prices)

        empty = [0] * size
        buy = [0] *size
        sell = [0] * size

        buy[0] = -prices[0]
        for i in range(1,size):
            empty[i] = max(empty[i-1],sell[i-1])
            buy[i] = max(buy[i-1],empty[i-1]-prices[i],sell[i-1]-prices[i])
            sell[i] = buy[i-1]+prices[i] -fee

        return max(sell[size-1],empty[size-1])
```
