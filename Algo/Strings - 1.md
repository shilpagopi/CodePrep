# Strings
### At a Glance: 
> #### **Question-Patterns**  
> * DP
> * Rotation -> Concatenation
> * Trie
> * DP equations for a) longest palindromic substring b) longest palindromic subsequence c) longest common substring d) longest common subsequence.
<br>If single/same string: consider inner substring (i+1,j-1) and add 2 if s[i]==s[j] 
<br>If two strings: consider till last index (i-1,j-1) and add 1 if s[i]==s[j]
<br>If subsequence and s[i]!=s[j], consider i+-1,j and i,j-1. 
<br>If substring and s[i]!=s[j], restart from 0.
<br>Take max/min of all cells. Cells can be length of string or true/false.
---

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

#### Wildcard match
*Question-Pattern* : DP, Wildcard Match
```java
public static boolean isMatch(String str, int n, String pattern, int m, Map<String, Boolean> lookup)
{
    String key = n + "|" + m;
    if (lookup.containsKey(key)) 
        return lookup.get(key);
        
    if (m == pattern.length())
    {
        lookup.put(key, (n == str.length()));
        return n == str.length();
    }

    // if the input string reaches its end, return when the
    // remaining characters in the pattern are all `*`
    if (n == str.length())
    {
        for (int i = m; i < pattern.length(); i++)
        {
            if (pattern.charAt(i) != '*')
            {
                lookup.put(key, false);
                return false;
            }
        }
        lookup.put(key, true);
        return true;
    }

    if (pattern.charAt(m) == '?' || pattern.charAt(m) == str.charAt(n))
        lookup.put(key, isMatch(str, n + 1, pattern, m + 1, lookup));
    else if (pattern.charAt(m) == '*')
        lookup.put(key, isMatch(str, n + 1, pattern, m, lookup) || isMatch(str, n, pattern, m + 1, lookup)); //skip * or skip string char
    else 
        lookup.put(key, false);

    return lookup.get(key);
}
```
Time: O(N * M), Space: O(N * M)

#### Min Deletions to convert a String to Palindrome
*QuestionPattern* : DP
```java
if (X[i] == X[j])
    dp[i][j] = dp[i + 1][j - 1]
else 
    dp[i][j] = 1 + min(dp[i][j-1],dp[i-1][j])
```
           
#### Check palindrome in O(1) space
*QuestionPattern* : Centering of palindromes
Check for expand(str,i,i) and expand(i,i+1)
```java
public static boolean expand(String str, int low, int high)
{
    int len = str.length();
    while (low >= 0 && high < len &&
            (str.charAt(low) == str.charAt(high))) {
        low--;
        high++;
    }
    return low==-1 && high==len;
}
 ```
