# [Tree: Preorder Traversal](https://www.hackerrank.com/challenges/tree-preorder-traversal/problem)

![image](Problem.png)



### My Answer

```python
def preOrder(root):
    print(root.info,end=' ')
    if root.left : 
        preOrder(root.left)
    if root.right : 
        preOrder(root.right)
```

* Time Complexity : O(n)
* Space Complexity : O(n)



### The things I got
