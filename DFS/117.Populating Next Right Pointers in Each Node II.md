```
# Definition for binary tree with next pointer.
# class TreeLinkNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
#         self.next = None

class Solution:
    # @param root, a tree link node
    # @return nothing
    def connect(self, root):
        
        rights = {}
        self.dfs(root,0,rights)

    def dfs(self,root,level,rights):
        if not root:
            return

        self.dfs(root.right,level+1,rights)
        next_right = rights.get(level)
        root.next = next_right
        rights[level] = root
        self.dfs(root.left,level+1,rights)
```
