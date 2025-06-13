# Dynamic Programming
### General Tips:
> If only previous row is used, use 1-D array
> If target variable is continuous and limited, use 2-D array pattern:
> * Options on row and target in columns
> * If options can be reused infinitely: consider [i][j-optionvalue] term
> * If options can be used only once: consider [i-1][j-optionvalue] term
> * If option can be skipped: consider [i-1][j] term
> * If option has a cost, add or multiply it alongwith the [j-optionvalue] term
> If target variable is non-continuous, try using induction. 

#### Find min/max cost/path/sum to reach Target
Choose minimum (maximum) path among all possible paths before the current state, then add value for the current state
> routes[i] = min(routes[i-1], routes[i-2], ... , routes[i-k]) + cost[i]

```
for (int i = 1; i <= target; ++i) {
   for (int j = 0; j < ways.size(); ++j) {
       if (ways[j] <= i) {
           dp[i] = min(dp[i], dp[i - ways[j]] + cost / path / sum) ;
       }
   }
}
``` 
Approaching from target backwards:
Think max/min dist from here(curr cell) to target, return dp[0][0] as ans.

#### Distinct ways to reach target
Sum all possible ways to reach the current state.

> routes[i] = routes[i-1] + routes[i-2], ... , + routes[i-k]
```
for (int i = 1; i <= target; ++i) {
   for (int j = 0; j < ways.size(); ++j) {
       if (ways[j] <= i) {
           dp[i] += dp[i - ways[j]];
       }
   }
}
```

If a 4 way matrix: use filltype or graph.
When using dp for graph,
```python 
def dfs(src):
   if dp[src] is not None:
       return dp[src]
   val=0
   for adj in graph[src]:
       val+=dfs(adj)
   dp[src] = val #update as postconpute only after all further paths are traversed.
```
#### Given two strings s1 and s2, return some result.
Most of the problems on this pattern requires a solution that can be accepted in O(n^2) complexity.
```
for (int i = 0; i < n; ++i) {
   for (int j = 0; j < m; ++j) {
       if (s1[i] == s2[j]) {
           dp[i][j] = /*code*/;
       } else {
           dp[i][j] = /*code*/;
       }
   }
}
```

#### Decision Making
An option to choose or ignore the current value  
Draw option pathways and choose the best (eg. alternate house robber problem)  

#### Fibonacci style
Eg.Pairing n friends
```
f(n) = f(n - 1) + (n - 1) * f(n - 2)
``` 

#### 1-D Array DP 
Eg. Coin change with infinite coins
```
for (int i=0; i<coins.size(); i++)
    for (int j=coins[i]; j<=n; j++)
            table[j] += table[j-S[i]];
 ```
 
#### 1-D Array DP with Extra Cost Term
Eg.Rod Cutting
```
1D : dp[i][j]=max(dp[i][j],dp[i][j-rodlen[j]]+price[rodlen[j]])
```

#### Dice Throw Sum
Number of ways of achieving target sum S by rolling n dice together:
```
    for (int i = 2; i <= n; i++)
        for (int j = 1; j <= S; j++)
            for (int k = 1; k <= 6 && k < j; k++)
                table[i][j] += table[i-1][j-k];
```

#### Count number of Strictly Increasing Subarrays 
*QuestionPattern*: Answer is sum of values of DP cells
```java
int getCount(int arr[], int n)
{
    int count = 0; //answer
    int len = 0; //number of arrays ending at previous index
 
    for (int i = 1; i < n; i++)
    {
        if (arr[i - 1] < arr[i])       
            count += (++len);
        else 
            len = 0; 
    } 
    return count;
}
```
#### Longest Palindromic Subsequence (Non-continuous)
*QuestionPattern*: DP
```
if X[i]==X[j] 
   dp[i][j]=dp[i+1][j-1]+2
else 
   dp[i][j] = max(dp[i-1][j],dp[i][j-1])
```   
### Count the number of times a pattern appears in a string as subsequence
*QuestionPattern*: DP
```
T[i][j] = ((X[i] == Y[j]) ? T[i - 1][j - 1] : 0) + T[i - 1][j];
```

Alternative:   
Eg. "sue" in "subsequence" 7 times.  
Traverse "subsequence". Store in an array the number of sequences ending at each letter of pattern until current element.   
If "e" is found, e_count += u_count
