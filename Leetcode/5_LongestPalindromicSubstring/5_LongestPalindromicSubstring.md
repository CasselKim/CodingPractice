# [5. Longest Palindromic Substring](https://leetcode.com/problems/longest-palindromic-substring/)

![image](Problem.png)



### My Answer

```python
class Solution:
    def longestPalindrome(self, s: str) -> str:
        if len(s)==1 : return s
        l,r = 0,0
        longest = ''
        for i in range(len(s)-1) : 
            res1=''
            if s[i]==s[i+1] : 
                res1 = self.spread(s,i,i+1)
            res2 = self.spread(s,i,i) 
            res = max(res1,res2,key=len)
            
            if len(res) > len(longest) : 
                longest = res
        return longest
        
    def spread(self,string:str,l:int,r:int) -> str: 
        while 0<=l and r<len(string) and string[l]==string[r] : 
            l-=1
            r+=1
        palindromic = string[l+1:r]
        return palindromic
```

* Time Complexity : O(n) ~ O(n^2)
* Space Complexity : O(n)



### The things I got
