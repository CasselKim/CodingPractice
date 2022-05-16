# [45. Jump Game II](https://leetcode.com/problems/jump-game-ii/)

![image](Problem.png)



### My Answer

```python
def jump(self, nums: List[int]) -> int:
	dp = [0 for _ in range(len(nums))]
	for i in range(len(nums)) : 
		for j in range(1,nums[i]+1) : 
			if i+j>=len(nums) : break
			elif dp[i+j]!=0 and dp[i+j]<=dp[i]+1 : continue
			else : 
            	dp[i+j]=dp[i]+1
	return dp[-1]
```

* Time Complexity : O(a*b)
* Space Complexity : O(a)



### The things I got
