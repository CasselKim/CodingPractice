# [Maximum Xor](https://www.hackerrank.com/challenges/maximum-xor/problem)

![image](Problem.png)



### My Answer

```python
def maxXor(arr, queries):
    result = []
    for q in queries : 
        maximum = 0
        for x in arr : 
            if x^q > maximum : 
                maximum = x^q
        result.append(maximum)
    return result
```

* Time Complexity : O(n*m)
* Space Complexity : O(n)



### The things I got
