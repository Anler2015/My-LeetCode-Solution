```
import collections
class Solution:
    def findSubstring(self, s, words):
        """
        :type s: str
        :type words: List[str]
        :rtype: List[int]
        """
        if not s or not words:
            return []

        res  = []
        dic = collections.defaultdict(int)
        for i in words:
            dic[i] = dic[i] + 1

        word_nums = len(words)
        word_length = len(words[0])
        str_length = len(s)

        for i in range(0,str_length- word_length*word_nums+1):
            local_dic = dic.copy()
            count = word_nums
            start = i
            while count > 0:
                curstr = s[start:start+word_length]
                if local_dic[curstr] <= 0:
                    break
                local_dic[curstr] = local_dic.get(curstr) - 1
                count -= 1
                start += word_length

            if count == 0:  res.append(i)

        return res
```
