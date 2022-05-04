# [16. 3Sum Closest](https://leetcode.com/problems/3sum-closest/)

![image](Problem.png)



### My Answer

```python
from functools import reduce

class Solution:

    def threeSumClosest(self, nums: List[int], target: int) -> int:
        two_sum = [x-target for x in nums]
        
        closet_zero = reduce(lambda a,b:min(abs(a),abs(b)),nums)
        sorted_nums = sorted(nums)
        l, r = 0,len(sorted_nums)-1
        m = r//2
        for i in range(len(sorted_nums)) : 
            if sorted_nums[i]==closet_zero : 
                l=i-1
                m=i
                r=i+1
        
        min_gap = 10000
        left_one, right_one = sorted_nums[l], sorted_nums[r]
        while 0<=l<r<len(sorted_nums) : 
            if closet_zero-(sorted_nums[l]+sorted_nums[r])<min_gap : 
                min_gap = closet_zero-(sorted_nums[l]+sorted_nums[r])
                left_one, right_one = sorted_nums[l], sorted_nums[r]
            while 0<l and sorted_nums[l-1]==sorted_nums[l] : 
                l-=1
            while r<len(sorted_nums)-1 and sorted_nums[r]==sorted_nums[r+1] :
                r+=1
        return min_gap+target
                
        
```

* Time Complexity : O(-)
* Space Complexity : O(-)



### The things I got
