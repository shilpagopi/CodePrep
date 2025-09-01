# Coding Tips
* Use list splicing for easy permutation combination
* Trie = {}, curr = Trie, curr[child] = {} #Trie implementation 
* Use enumerate: for i, val in enumerate(list):
* ord('a'),chr(97)
* strg[i]='c' is not supported in python. convert string to list. 
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
* for object, use not obj. for values, be explicit in differentiating between val is None or val==0. (don't use "if val")
* Tuple iteration: ls = [('a',1),('b',2)] for x,y in ls:....

```
from collections import Counter
my_list = ['apple', 'banana', 'apple', 'orange', 'banana', 'apple']
fruit_counts = Counter(my_list)
print(fruit_counts) # Output: Counter({'apple': 3, 'banana': 2, 'orange': 1})

# From a string
my_string = "mississippi"
letter_counts = Counter(my_string)
```

```
### List Equivalence
list1 = [1, 2, 3]
list2 = [1, 2, 3]
list3 = [3, 2, 1]
print(list1 is list2) # Output: False
print(list1 == list2) # Output: True # order-sensitive
print(list1 == list3) # Output: False
print(sorted(list1)==sorted(list3)) # Output: True

# is vs. ==: is checks memory objetc equivalence

### Set Equivalence
listX = [1, 2, 2, 3]
listY = [2, 1, 3]

print(set(listX) == set(listY)) # Output: True

### Dict Equivalence

dict1 = {'a': 1, 'b': 2, 'c': 3}
dict2 = {'c': 3, 'a': 1, 'b': 2}  # Same content, different order
dict3 = {'a': 1, 'b': 2, 'd': 4}  # Different keys
dict4 = {'a': 1, 'b': 5, 'c': 3}  # Different values

print(f"dict1 == dict2: {dict1 == dict2}") #True # order-insensitive
print(f"dict1 == dict3: {dict1 == dict3}") #False
print(f"dict1 == dict4: {dict1 == dict4}") #False
# in ==, both keys and corresponding values are checked.
```

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
