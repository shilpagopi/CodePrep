# Coding Tips
* Use list splicing for easy permutation combination
* Trie = {}, curr = Trie, curr[child] = {} #Trie implementation 
* Use enumerate: for i, val in enumerate(list):
* ord('a'),chr(97)
* float('inf') for extreme values
* Floor division operator: x // y: 5/2=2, -5//2=-3
* Exponential: a_cube = a**3
* Modulo: 10^9+7 is close to 2^30 \
( a + b) % c = ( ( a % c ) + ( b % c ) ) % c \
( a * b) % c = ( ( a % c ) * ( b % c ) ) % c \
( a – b) % c = ( ( a % c ) – ( b % c ) ) % c \
Not valid for division
* math.ceil(x), math.floor(x)

``` python
def factorial( n) :
    M = 1000000007
    f = 1
 
    for i in range(1, n + 1): 
        f = (f * i) % M # Now f never can 
                        # exceed 10^9+7 
 
    return f 
```

