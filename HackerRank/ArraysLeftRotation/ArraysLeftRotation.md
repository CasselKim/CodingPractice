# [Arrays : Left Rotation](https://www.hackerrank.com/challenges/ctci-array-left-rotation/problem?h_l=interview&playlist_slugs%5B%5D=interview-preparation-kit&playlist_slugs%5B%5D=arrays)

![image](Problem.png)



### My Answer

```python
def rotLeft(a, d):
    for _ in range(d) : a.append(a.pop(0))
    return a
```

* Time Complexity : O(n)
* Space Complexity : O(1)



### The things I got
