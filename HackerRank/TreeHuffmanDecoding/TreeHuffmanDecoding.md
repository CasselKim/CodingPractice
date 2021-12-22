# [Tree: Huffman Decoding](https://www.hackerrank.com/challenges/tree-huffman-decoding/problem)

![image](Problem.png)



### My Answer

```python
def decodeHuff(root, s):
    head = root
    result = ''
    for i in range(len(s)) : 
        if s[i]=='0' and head.left : 
            head=head.left
        elif s[i]=='1' and head.right : 
            head=head.right
        else : 
            result+=head.data
            head=root
            if s[i]=='0' : head=head.left
            else : head=head.right
    result+=head.data
    print(result)
```

* Time Complexity : O(n)
* Space Complexity : O(1)



### The things I got
