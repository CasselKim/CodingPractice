# [[7 Kyu] Alternate capitalization](https://www.codewars.com/kata/59cfc000aeb2844d16000075/train/python)

![image](./Problem.png)


## Instructions

### Task

Given a string, capitalize the letters that occupy even indexes and odd indexes separately, and return as shown below. Index `0` will be considered even.

For example, `capitalize("abcdef") = ['AbCdEf', 'aBcDeF']`. See test cases for more examples.

The input will be a lowercase string with no spaces.

Good luck!



## Sample Test

```python
Test.it("Basic tests")
Test.assert_equals(capitalize("abcdef"),['AbCdEf', 'aBcDeF'])
Test.assert_equals(capitalize("codewars"),['CoDeWaRs', 'cOdEwArS'])
Test.assert_equals(capitalize("abracadabra"),['AbRaCaDaBrA', 'aBrAcAdAbRa'])
Test.assert_equals(capitalize("codewarriors"),['CoDeWaRrIoRs', 'cOdEwArRiOrS'])
```



## My solution

```python
def capitalize(s):
    return [''.join([x if i%2 else x.upper() for i,x in enumerate(s)]),
            ''.join([x if not i%2 else x.upper() for i,x in enumerate(s)])]
```



## Test Results

Test Passed

Test Passed

Test Passed

You have passed all of the tests! :)

---------

Time: 823ms Passed: 106 Failed: 0



## Best Solution

```python
def capitalize(s):
    s = ''.join(c if i%2 else c.upper() for i,c in enumerate(s))
    return [s, s.swapcase()]
```



## The things I got

**string.swapcase()** : Convert case from upper to lower, lower to upper.