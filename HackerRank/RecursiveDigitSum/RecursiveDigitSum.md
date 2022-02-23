# [Recursive Digit Sum](https://www.hackerrank.com/challenges/recursive-digit-sum/problem)

![image](Problem.png)



### My Answer

```python
def superDigit(n, k):
    x = int(n)%9*k%9
    return x if x else 9
```

* Time Complexity : O(1)
* Space Complexity : O(1)



### The things I got
