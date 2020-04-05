# [[7 Kyu] Find the area of the rectangle!](https://www.codewars.com/kata/580a0347430590220e000091/train/python)

![image](./Problem.png)


## Instructions

Find the area of a rectangle when provided with one diagonal and one side of the rectangle. If the input diagonal is less than or equal to the length of the side, return "Not a rectangle". If the resultant area has decimals round it to two places.

```python
This kata is meant for beginners. Rank and upvote to bring it out of beta!
```



## Sample Test

```python
@test.describe('Example Tests')
def example_tests():
    @test.it('Example Test Case')
    def example_test_case():
        test.assert_equals(area(5, 4), 12);
        test.assert_equals(area(10, 6), 48);
        test.assert_equals(area(13, 5), 60);
        test.assert_equals(area(12, 5), 54.54);
        
    @test.it('Fixed Test Case')
    def fixed_test_case():
        test.assert_equals(area(5, 5), "Not a rectangle");
        test.assert_equals(area(3, 5), "Not a rectangle");

```



## My solution

```python
from math import sin,acos

def area(d, l): 
    if d<=l : return 'Not a rectangle'
    else : return float('%.2f' %(d*l*sin(acos(l/d))))
```



## Test Results

Test Passed

Test Passed

Test Passed

You have passed all of the tests! :)

---------

Time: 878ms Passed: 106 Failed: 0



## Best Solution

```python
def area(d, l): 
    return "Not a rectangle" if d<=l else round( l*(d*d-l*l)**.5, 2)
```



## The things I got

**round(number, digit)** : rounding number by given digit