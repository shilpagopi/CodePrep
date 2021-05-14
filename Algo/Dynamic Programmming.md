# Dynamic Programming
### General Tips:
> If only previous row is used, use 1-D array
> In 2-D array pattern problems:
> * Options on row and target in columns
> * If options can be reused infinitely: consider [i][j-optionvalue] term
> * If options can be used only once: consider [i-1][j-optionvalue] term
> * If option can be skipped: consider [i-1][j] term
> * If option has a cost, add or multiply it alongwith the [j-optionvalue] term.

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
