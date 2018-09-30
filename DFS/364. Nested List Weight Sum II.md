```
# """
# This is the interface that allows for creating nested lists.
# You should not implement it, or speculate about its implementation
# """
#class NestedInteger:
#    def __init__(self, value=None):
#        """
#        If value is not specified, initializes an empty list.
#        Otherwise initializes a single integer equal to value.
#        """
#
#    def isInteger(self):
#        """
#        @return True if this NestedInteger holds a single integer, rather than a nested list.
#        :rtype bool
#        """
#
#    def add(self, elem):
#        """
#        Set this NestedInteger to hold a nested list and adds a nested integer elem to it.
#        :rtype void
#        """
#
#    def setInteger(self, value):
#        """
#        Set this NestedInteger to hold a single integer equal to value.
#        :rtype void
#        """
#
#    def getInteger(self):
#        """
#        @return the single integer that this NestedInteger holds, if it holds a single integer
#        Return None if this NestedInteger holds a nested list
#        :rtype int
#        """
#
#    def getList(self):
#        """
#        @return the nested list that this NestedInteger holds, if it holds a nested list
#        Return None if this NestedInteger holds a single integer
#        :rtype List[NestedInteger]
#        """

class Solution:
    maxdepth = 0
    def depthSumInverse(self, nestedList):
        """
        :type nestedList: List[NestedInteger]
        :rtype: int
        """
        self.getDepth(nestedList,1)
        
        return self.getSum(nestedList,self.maxdepth)
    
    def getSum(self,nestedList,depth):
        if not nestedList:
            return 0
        sum = 0
        for i in nestedList:
            if i.isInteger():
                sum += i.getInteger() * depth
            else:
                sum += self.getSum(i.getList(),depth -1)
        return sum
        
    def getDepth(self,nestedList,level):
        self.maxdepth = max(self.maxdepth,level)
        for i in nestedList:
            if not i.isInteger():
                self.getDepth(i.getList(),level +1)
                
        
    
        
```
