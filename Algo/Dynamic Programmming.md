# Dynamic Programming

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


