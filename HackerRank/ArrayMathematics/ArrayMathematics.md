# [Any or All](https://www.hackerrank.com/challenges/any-or-all/problem)

![image](Problem.png)



### My Answer

```python
n, integers = input(), input().split(' ')
cond1 = all([int(x)>0 for x in integers])
cond2 = any([x==x[::-1] for x in integers])
print(cond1 and cond2)
```

* Time Complexity : O(2n)
* Space Complexity : O(n)



### The things I got
