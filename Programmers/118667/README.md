# [두 큐 합 같게만들기](https://school.programmers.co.kr/learn/courses/30/lessons/118667)



### My Answer

```python
from collections import deque

class node : 
    def __init__(self, v) : 
        self.v = v

def solution1(queue1, queue2):
    
    deq1 = deque([node(x) for x in queue1])
    deq2 = deque([node(x) for x in queue2])
    
    sum1 = sum(queue1)
    sum2 = sum(queue2)

    S = set()
    
    res = 0
    while True : 

        while sum1<sum2 : 
            poped = deq2.popleft()
            sum2 -= poped.v
            sum1 += poped.v
            deq1.append(poped)
            res+=1
        
        if sum1==sum2 : return res
        if deq1 and deq2 :
            if (deq1[0],deq2[0]) in S : break
            S.add((deq1[0],deq2[0]))
        
        while sum1>sum2 : 
            poped = deq1.popleft()
            sum1 -= poped.v
            sum2 += poped.v
            deq2.append(poped)
            res+=1
            
        if sum1==sum2 : return res
        if deq1 and deq2 :
            if (deq1[0],deq2[0]) in S : break
            S.add((deq1[0],deq2[0]))
    
        
    return -1
        
        
def solution(queue1, queue2):
    
    deq1 = deque(queue1)
    deq2 = deque(queue2)
    deq3 = deque(queue1)
    deq4 = deque(queue2)
    
    sum1 = sum(deq1)
    sum2 = sum(deq2)
    sum3 = sum1
    sum4 = sum2
    
    res = 0
    while True : 

        ##### fast part #####
        while sum3<sum4 : 
            poped = deq4.popleft()
            sum4 -= poped
            sum3 += poped
            deq3.append(poped)
            res+=1
            
        if sum3==sum4 : return res
            
        while sum3>sum4 : 
            poped = deq3.popleft()
            sum3 -= poped
            sum4 += poped
            deq4.append(poped)
            res+=1
            
        if sum3==sum4 : return res
     
        while sum3<sum4 : 
            poped = deq4.popleft()
            sum4 -= poped
            sum3 += poped
            deq3.append(poped)
            res+=1
            
        if sum3==sum4 : return res
            
        while sum3>sum4 : 
            poped = deq3.popleft()
            sum3 -= poped
            sum4 += poped
            deq4.append(poped)
            res+=1
            
        if sum3==sum4 : return res
    
        ##### slow part #####
        while sum1<sum2 : 
            poped = deq2.popleft()
            sum2 -= poped
            sum1 += poped
            deq1.append(poped)
        
        while sum1>sum2 : 
            poped = deq1.popleft()
            sum1 -= poped
            sum2 += poped
            deq2.append(poped)
    
        ## loop check
        if sum1==sum3 and sum2==sum4 and len(deq1)==len(deq3) and len(deq2)==len(deq4): 
            if deq1==deq3 : 
                return -1

    return -1
```

* Time Complexity : O(2n)
* Space Complexity : O(2n)



### The things I got
