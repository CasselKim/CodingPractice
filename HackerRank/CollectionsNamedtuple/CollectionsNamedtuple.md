# [Collections namedtuple()](https://www.hackerrank.com/challenges/py-collections-namedtuple/problem)  

![image](Problem.png)



### My Answer

```python
import sys
from collections import namedtuple

counts = int(sys.stdin.readline())
col = list(filter(lambda x : x, sys.stdin.readline().replace('\n','').split(' ')))

Student = namedtuple('Student',col)
total=0
for i in range(counts) : 
    info = list(filter(lambda x : x, sys.stdin.readline().replace('\n','').split(' ')))
    ID = col.index('ID')
    MARKS = col.index('MARKS')
    NAME = col.index('NAME')
    CLASS = col.index('CLASS')
    
    student_A = Student(ID = info[ID],
                        MARKS = info[MARKS],
                        NAME = info[NAME],
                        CLASS = info[CLASS])
                      
    total += int(student_A.MARKS)

average = '%.2f' %(total/counts)
print(average)
```

* Time Complexity : O(n)
* Space Complexity : O(n)



```python
# 4 line code
import sys
from collections import namedtuple

table = [list(filter(lambda x : x,sys.stdin.readline().replace('\n','').split(' '))) for _ in range(int(sys.stdin.readline())+1)]
Student = namedtuple('Student',table[0])
print('%.2f'%(sum([int(Student(*table[i]).MARKS) for i in range(1,len(table))])/(len(table)-1)))
```

* Time Complexity : O(n)
* Space Complexity : O(n)



### The things I got
