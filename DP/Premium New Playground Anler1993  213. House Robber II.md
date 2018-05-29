```
class Solution:
    def rob(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        
        size = len(nums)
        if size == 0:
            return 0
        elif size ==1:
            return nums[0]
            
         # 从（0 到n-1） 和 （1到n） 之间 取最大值即可
        return max(self.robone(nums[0:size-1]),self.robone(nums[1:size]))
    
    def  robone(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        size = len(nums)
        if size == 0:
            return 0
        elif size==1:
            return nums[0]
        elif size ==2:
            return max(nums[0],nums[1])

        dp=[0 for i in range(size)]

        dp = nums[:]

        if nums[0]+nums[2] >nums[1]:
            dp[2] = nums[0]+nums[2]

        for i in range(3,size):
            dp[i]=max(dp[i-2],dp[i-3])+nums[i]

        res = 0
        for i in range(size):
            res= max(res,dp[i])

        return res
```
