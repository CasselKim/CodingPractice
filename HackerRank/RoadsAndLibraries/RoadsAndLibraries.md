# [Roads And Libraries](https://www.hackerrank.com/challenges/torque-and-development/problem)

![image](Problem.png)



### My Answer

```python

def makeGraph(cities) : 
    G = defaultdict(set)
    for city in cities : 
        G[city[0]].add(city[1])
        G[city[1]].add(city[0])
    return G


def roadsAndLibraries(n, c_lib, c_road, cities):
    if c_lib < c_road: return c_lib * n
    G = makeGraph(cities)
    used = set()

    total = (n-len(G.keys()))*c_lib
    for key in list(G.keys()) : 
        if key in used : continue
        else : 
            stack = [key]
            seen = set([key])
            counting_star = 0

            while stack : 
                pop_key = stack.pop()
                for x in G[pop_key] : 
                    if x not in seen : 
                        seen.add(x)
                        used.add(x)
                        stack.append(x)
                        counting_star+=1

            total+=counting_star*c_road+c_lib

    return total
```

* Time Complexity : O(n)
* Space Complexity : O(2n)



### The things I got

그래프를 시작했다. 감 잡기가 어려워 Discussion을 많이 참고하는중  

해당 문제는 그래프 알고리즘이라기 보단 DFS를 써서 어떻게 creative하게 푸냐의 문제인거같음..  

나는 파이썬의 set.union의 시간복잡도를 예상못해서 계속 timeout이 나왔는데, O(len(s)+len(t))의 어마무시한 놈이었다. **set은 hash기반이라서 굉장히 빠르지만 union이나 intersection과 같은 작업에서는 굉장히 느려지니 잘 사용하도록 하자.**  

