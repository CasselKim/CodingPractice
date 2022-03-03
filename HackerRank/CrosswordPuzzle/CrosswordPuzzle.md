# [Crossword Puzzle](https://www.hackerrank.com/challenges/crossword-puzzle/problem)





### My Answer

```python
def crosswordPuzzle(crossword, words):

    crossword_list = [list(c) for c in crossword]
    
    
    horizon = []
    for i in range(len(crossword)) : 
        temp = []
        for j in range(len(crossword[0])) : 
            if crossword[i][j]=='-' : 
                temp.append((i,j))
            else : 
                horizon.append(temp)
                temp=[]
        horizon.append(temp)
        
    vertical = []
    for j in range(len(crossword[0])) : 
        temp = []
        for i in range(len(crossword)) : 
            if crossword[i][j]=='-' : 
                temp.append((i,j))
            else : 
                vertical.append(temp)
                temp=[]
        vertical.append(temp)
        
    horizon = [x for x in horizon if len(x)>1 ]
    vertical = [x for x in vertical if len(x)>1 ]
    
    length_dict = defaultdict(list)
    for x in horizon+vertical : 
        length_dict[len(x)].append(x)
        
    word_dict = defaultdict(list)
    for y in words.split(';') : 
        word_dict[len(y)].append(y)
        
    pair_dict = defaultdict(list)
    for k in range(1,11) : 
        for p in list(permutations(word_dict[k],len(word_dict[k]))) : 
            if length_dict[k] : 
                pair_dict[k].append(list(zip(list(p),length_dict[k])))
                
        
        for x in pair_dict[k] : 
            for y in x : 
                is_error = False
                for i,z in enumerate(y[1]) : 
                    if crossword_list[z[0]][z[1]] != '-' and crossword_list[z[0]][z[1]] != y[0][i] : 
                        is_error = True
                        break
                    else : 
                        crossword_list[z[0]][z[1]] = y[0][i]
                if is_error : break
            if is_error : break
            
    print('\n'.join([''.join(c) for c in crossword_list]))
```

* Time Complexity : O(n)
* Space Complexity : O(n)



### The things I got
