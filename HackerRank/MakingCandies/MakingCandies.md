# [Making Candies](https://www.hackerrank.com/challenges/making-candies/problem)

![image](Problem.png)



### My Answer

```python
def minimumPasses(m, w, p, n):
    candy = 0
    invest = 0
    spend = sys.maxsize
    while candy < n:
        passes = (p - candy) // (m * w)
        if passes <= 0:
            mw = (candy // p) + m + w
            half = math.ceil(mw / 2)
            if m > w:
                m = max(m, half)
                w = mw - m
            else:
                w = max(w, half)
                m = mw - w
            candy %= p
            passes = 1
        candy += passes * m * w
        invest += passes
        spend = min(spend, invest + math.ceil((n - candy) / (m * w)))
    return min(invest, spend)
```

* Time Complexity : O(n)
* Space Complexity : O(2n)



### The things I got
