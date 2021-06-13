# Strings
> #### **Question-Patterns**  
> * DP
> * Rotation -> Concatenation
> 

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
