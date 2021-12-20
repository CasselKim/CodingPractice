# [Abbreviation](https://www.hackerrank.com/challenges/abbr/problem)

![image](Problem.png)



### My Answer

```python
def resetQueue(q, array) : 
    while q.qsize() : 
        q.get()
    for x in array :
        q.put(x)

def abbreviation(a, b):
    #print('---------------')
    q = queue.Queue()
    resetQueue(q, b)          
        
    previous_lower = ''
    next_letter = q.get()
    count=0
    for i,x in enumerate(a) : 
        #print('x : {}, next : {}, previous_lower : {}'.format(x,next_letter,previous_lower))
        if x.upper()==next_letter : 
            if x.islower() :
                previous_lower = x
            count+=1
            if q.qsize()==0 : 
                next_letter = '?'
                continue
            else : 
                next_letter = q.get()
        elif x.isupper() and x == previous_lower.upper() : 
            previous_lower = ''
        elif x==x.upper() : 
            print('splash! at x : {}, next_letter : {} // i : {}'.format(x,next_letter,i))
            resetQueue(q, b)
            count=0
    #print(count)
    if count==len(b) : 
        return 'YES'
    else : 
        return 'NO'
```

* Time Complexity : O(n)
* Space Complexity : O(2n)



### The things I got

일단 n으로 풀긴 했지만 대문자를 기준으로 DP를 작성해야 할 듯 싶다.  

1차 풀이 : B를 순회하면서 q에 넣고 -> pull하면서 대문자랑 맞는지 확인. 소문자면 간직해뒀다가 대문자가 나왔을 때 1회 면제용으로 사용.  

리뷰 : 쉽게볼게 아닌 것 같다. 뒤에서 대문자가 나온게 3번째 H인지 15번째 H인지 모른다. 흐음  