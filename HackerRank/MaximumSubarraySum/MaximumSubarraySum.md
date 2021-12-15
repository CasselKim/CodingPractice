# [Maximum Subarray Sum](https://www.hackerrank.com/challenges/maximum-subarray-sum/problem)

![image](Problem.png)



### My Answer

```python
import bisect

def maximumSum(a, m):
    maximum,prefix=0,0
    a1=[]
    for x in a:
        prefix=(prefix+x)%m
        maximum=max(maximum,prefix)
        
        #find the one step bigger value than prefix
        index=bisect.bisect_left(a1,prefix+1)
        
        #if prefix is not biggest
        if(index<len(a1)):
            #compare with maximum and step size
            maximum=max(maximum,prefix-a1[index]+m)
            
        bisect.insort(a1,prefix)
    return maximum
```

* Time Complexity : O(nlog(n))
* Space Complexity : O(n)



### The things I got

naiive 풀이방법 : nlog(n)  

n으로 끝낼 방법을 찾아야한다.  

단서1번) subarray가 붙어있다. subset개념이 아님.  

단서2번) m이 10^14이므로 modulo list를 만들어서 하는 것도 아님. space complexity에 위반  

단서3번) array에 모두 modulo 연산을 한 다음에 시행해도 결과는 똑같음.  

---

카데인 알고리즘 (Maximum Subarray)의 심화버전이라고 볼 수 있다. 기본적으로 카데인 알고리즘을 따르지만 modulo라는 추가 조건으로 인해서 살짝 꼬아준다. 바로 다음 element가 maximum보다 크다해도 실제로는 크지 않을 수 있으므로 index-base가 아닌 value-base로 접근한다.  

원래 카데인 알고리즘 : max(A[i],A[i]+A[i-1]  

modulo 카데인 : max(maximum, prefix와 prefix보다 한 스탭 더 큰거)  

왜냐하면 그래야지 마이너스 최소값이 나올텐데 이게 modulo 최대값이기 때문  

Ex) 4-5=-1 -> modulo-1이니까 최댓값  

Ex) 4-9=-5 -> modulo-5니까 개작음  

 