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

#### Coin Change
```
for (int i=0; i<coins.size(); i++)
    for (int j=coins[i]; j<=n; j++)
            table[j] += table[j-S[i]];
 ```
