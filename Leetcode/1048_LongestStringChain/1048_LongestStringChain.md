# [1048. Longest String Chain](https://leetcode.com/problems/longest-string-chain/)

![image](Problem.png)



### My Answer

```python
class Solution:
    def longestStrChain(self, words: List[str]) -> int:
        dp = {}
        res = 1
        for word in sorted(words, key=len):
            dp[word] = 1
            for i in range(len(word)):
                prev = word[:i] + word[i + 1 :]
                if prev in dp:
                    dp[word] = dp[prev] + 1
                    res = max(res, dp[word])

        return res	
```

* Time Complexity : O(nlog(n))
* Space Complexity : O(n)



### The things I got
