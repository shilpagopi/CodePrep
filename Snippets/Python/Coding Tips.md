# Coding Tips
* Use list splicing for easy permutation combination
* Trie = {}, curr = Trie, curr[child] = {} #Trie implementation 
* Use enumerate: for i, val in enumerate(list):
* ord('a'),chr(97)
* float('inf'),float('-inf') for extreme values
* Init 1d list: seen = [None] * 5 
* Init 2d list: matrix =[[0]*cols] * rows
* Floor division operator: x // y: 5/2=2, -5//2=-3
* Ceil division operator: -(-x//2)
* Exponential: a_cube = a**3
* Modulo: 10^9+7 is close to 2^30 \
( a + b) % c = ( ( a % c ) + ( b % c ) ) % c \
( a * b) % c = ( ( a % c ) * ( b % c ) ) % c \
( a – b) % c = ( ( a % c ) – ( b % c ) ) % c \
Not valid for division
* math.ceil(x), math.floor(x), math.pos(2,x), math.sqrt(x)

``` python
def factorial( n) :
    M = 1000000007
    f = 1
 
    for i in range(1, n + 1): 
        f = (f * i) % M # Now f never can 
                        # exceed 10^9+7 
 
    return f 
```
```python
# Looping from i = 5 to i = 2
for i in range(5, 1, -1):
    print(i)
```
```python
for n1, n2 in zip(nums1, nums2):
    print(n1, n2)
```
``` python

# Taking input as a number
number = int(input("Enter a number: "))

# Taking input as a string
string = input("Enter a string: ")

# Taking input as a list of numbers
numbers = input("Enter a list of numbers separated by spaces: ").split()
numbers = [int(x) for x in numbers]
```

#### TrieNode Declaration
```python
class TrieNode:
    def __init__(self,val,endmarker=False):
        self.val = val
        self.dct = {}
        self.endmarker = endmarker
```
