# [329. Longest Increasing Path In a Matrix](https://leetcode.com/problems/longest-increasing-path-in-a-matrix/)

![image](Problem.png)



### My Answer

```python
def longestIncreasingPath(self, matrix: List[List[int]]) -> int:
        m,n = len(matrix),len(matrix[0])
        Table = [[0 for _ in range(n)] for _ in range(m)]
        
        #traverse path count table
        def DFS(i,j) : 
            # has visit
            if Table[i][j] : 
                return Table[i][j]
            
            # traverse near node
            near = [0,0,0,0]
            if 0<i and matrix[i][j]<matrix[i-1][j] : #top
                near[0] = DFS(i-1,j)
            if i<m-1 and matrix[i][j]<matrix[i+1][j] : #down
                near[1] = DFS(i+1,j)
            if 0<j and matrix[i][j]<matrix[i][j-1] : #left
                near[2] = DFS(i,j-1)
            if j<n-1 and matrix[i][j]<matrix[i][j+1] : #right
                near[3] = DFS(i,j+1)
            
            # if any nearby node, return maximum.
            if any(near) : 
                Table[i][j]=max(near)+1
                return Table[i][j]
            else : # if no neighborhood (isolation), return 1(itself)
                Table[i][j]=1
                return 1
            
        maximum=0
        for i in range(m) : 
            for j in range(n) : 
                Table[i][j]=DFS(i,j)
                maximum = max(Table[i][j],maximum)

        return maximum
```

* Time Complexity : O(n*m)
* Space Complexity : O(n*m)



### The things I got

DFS Problem 유형 체크하자