# Strings
> #### **Question-Patterns**  
> * DP
> * Rotation -> Concatenation
> * Trie

#### Longest common string between 2 strings
*Question-Pattern* : DP
```java
init a[M+1][N+1] two dimensional matrix with [0]
for i in [0,M):
    for j in [i,N+1):
        if A[i]==B[j]:
            a[i+1][j+1]=a[i][j]+1
```   
O(N*M) instead of brute force (O(N*M^2)

#### Check if a string is a rotated palindrome
*Question-Pattern* : Rotation -> Concatenation
Check if longest palindromic substring of S+S is of length n.
Time: O(n^2), Space: O(n^2)

#### Lexicographic sorting of strings, Find maximum occurring word from list of string
*Question-Pattern* : Trie
DFS or Preorder traversal of trie
Time: O(N * M), Space: O(N * M) 
