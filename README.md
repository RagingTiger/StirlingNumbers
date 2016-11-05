##Purpose
This module was developed to make the generation of [Stirling numbers](https://en.wikipedia.org/wiki/Stirling_number) easy. The module
defines a function, [gen_stirling()](https://github.com/RagingTiger/StirlingNumbers/blob/631d76f217f83ebb441680f7417c6832514ee380/stirling.py#L16-L32), that returns a 2d list of the
numbers:

```python
def gen_stirling(n):
    '''
    Function to create Stirling numbers
    '''
    # initialize [n k] = [0 0] to 1
    s = [[1]]

    # building stirling triangle
    for i in range(1, n + 1):
        # initialize k=0 partition to 0
        r = [0]
        for k in range(1, i):
            r.append((i-1)*s[i-1][k] + s[i-1][k-1])
        r.append(1)
        s.append(r[:])
    # exit
    return s
```

## Usage
<p align="center">
  <img src="https://github.com/RagingTiger/gifs/raw/master/StirlingNumbers.gif"/>
</p>
The program can be executed from the commandline with one argument **"-n"** that
can be any integer value.

## Description
As the demo shows, the stirling.py module will create a 2d list of Stirling
numbers based on the **"-n"** value passed to the module:

```
n = 3

1
0 1
0 1 1
0 2 3 1

n = 5

1
0 1
0 1 1
0 2 3 1
0 6 11 6 1
0 24 50 35 10 1
```

The module can also be imported and used to generate Stirling numbers for
other applications, where **S[n][k]** means the Stirling number at **row = n**
and **column = k**:

```python
$ python
Python 2.7.12 (default, Oct 11 2016, 05:24:00)
[GCC 4.2.1 Compatible Apple LLVM 8.0.0 (clang-800.0.38)] on darwin
Type "help", "copyright", "credits" or "license" for more information.
>>> import stirling
>>> S = stirling.gen_stirling(5)
>>> S
[[1], [0, 1], [0, 1, 1], [0, 2, 3, 1], [0, 6, 11, 6, 1], [0, 24, 50, 35, 10, 1]]
>>> S[3][3]
1
>>> S[5][2]
50
>>>
```
