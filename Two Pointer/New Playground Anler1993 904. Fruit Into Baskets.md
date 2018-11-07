<https://leetcode.com/problems/fruit-into-baskets/description/>

```
class Solution:
    def totalFruit(self, tree):
        """
        :type tree: List[int]
        :rtype: int
        """
        i = j = 0
        res = 0
        basket = {}
        ans = 0
        while i < len(tree) and j < len(tree):
            if len(basket) <= 2:
                basket[tree[j]] = basket.get(tree[j],0) + 1
                j += 1
                res += 1
            else:
                basket[tree[i]] -= 1
                if basket[tree[i]] == 0:
                    basket.pop(tree[i])
                res -= 1
                i+=1
            if len(basket) <=2:
                ans = max(ans,res)
        return ans
       
        
```
