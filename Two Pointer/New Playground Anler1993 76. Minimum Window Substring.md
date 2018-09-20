超时
```
import collections
class Solution:
    def minWindow(self, s, t):
        """
        :type s: str
        :type t: str
        :rtype: str
        """
        if not s or not t:
            return ""

        dic = collections.defaultdict(int)
        count = 0
        for c in t:
            dic[c] += 1
            count += 1

        i,j = 0,0
        size = len(s)

        res = s
        flag = False
        while i - count < size and j < size:
            tempdic = dic.copy()
            tempcount = count
            while i < size and tempdic[s[i]] <= 0:
                i += 1

            j = i
            while tempcount > 0 and j < size:

                if tempdic[s[j]] > 0:
                    tempdic[s[j]] -= 1
                    tempcount -= 1
                j += 1


            if tempcount == 0:
                res = s[i:j] if j-i < len(res) else res
                flag = True
   
            i += 1
            j = i


        return res if flag else ""
```
