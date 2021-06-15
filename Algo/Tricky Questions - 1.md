# Tricky Questions
#### Nth Ugly Number : has prime factors 2,3,5 only
```
nthUglyNumber(int n)
{ 
    TreeSet<Long> t = new TreeSet<>();
    t.add(1L);
    int i = 1;
    while (i < n) {
        long temp = t.pollFirst();
        t.add(temp * 2);
        t.add(temp * 3);
        t.add(temp * 5);
        i++;
    }
    return t.pollFirst();
}
```    

#### Nth Catalan Number
```
int ans = 0;
for (int j = 0; j < N; j++)
    ans += catalan[j] * catalan[N - 1 - j];
```

#### Tiling Problem 
Ways of placing 2 x 1 tiles on 2 x N board: count(n) = count(n-1) + count(n-2)
 
#### SubSet Sum 
```
When an element can be used only once, dp[i][j] = dp[i-1][j] || dp[i-1][j-A[i-1]]
2 rows are sufficient
```

#### Partition a set into two subsets such that the difference of subset sums is minimum
s1 + s2 = TotalSum; the idea is find a feasible subset with sum closest to TotalSum/2.

#### Maximum Product Rod Cutting
* You need to make atleast 1 cut
* dp => max value attainable by atleast 1 cut
* If n==0 || n==1, return 0;
```
for(int i = 1 to l):
    for (int j = i to l):
        dp[j]=max(dp[j],i*(j-i),i*dp[j-i])
        dp is max of (without making a cut of length i, cut length i and not cuts in j-i, cut length i and cut length j-i)
```

### Generate n binary numbers
*QuestionPattern* : BFS of binary tree with every node 0 and 1.
```
q.append('1')
for i in range(n):
    front = str(q.popleft())
    q.append(front + '0')
    q.append(front + '1')
```
### Find correct order of alphabets in a given dictionary of ancient origin
*QuestionPattern* : Topological Sort of DAG
For every two adjacent words, consider an edge between first pair of mismatched characters
Time: O(N.M)

### Length of longest balanced parenthesis in a string
*QuestionPattern* : Replacement using +/-1, hashmap
1. Skip all )).. present at the start
2. Use hashmap to store earliest index of cumulative sum
3. Add 0 at -1th index
4. Find cumulative sum
