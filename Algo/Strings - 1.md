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

#### Edit Distance
Thought process: If comparing, "abc" to "acd", to compute [1][1], think "ab"->"a", "a"->"ac","a->a and b->c"

##### Case 1: Only Insertion Allowed
Consider A is shorter than B. This is only possible if A is a subsequence of B. If A is a subsequence of B, the edit distance is simply the difference in their lengths. If A is not a subsequence of B, the transformation is impossible, and the edit distance is infinite.

DP Table Formulation:
* Let dp[i][j] be the minimum number of insertions to transform the first i characters of string A (A[1..i]) into the first j characters of string B (B[1..j]).
* Base case: dp[0][0] = 0. dp[0][j] = j (insert j characters to get B[1..j]).
* Recurrence relation:
    * If A[i] == B[j], then dp[i][j] = dp[i-1][j-1] (no operation needed).
    * If A[i] != B[j], then dp[i][j] = dp[i][j-1] + 1 (insert B[j]).

Final answer: dp[m][n], where m and n are the lengths of A and B, respectively. If dp[m][n] is not equal to n-m (and A is a subsequence of B), then the transformation is impossible.

```
def isSubsequence(A, B):
    i, j = 0, 0
    while i < len(A) and j < len(B):
        if A[i] == B[j]:
            i += 1
        j += 1
    return i == len(A)
```

##### Case 2: Only Insertion and Deletion Allowed
Classic Longest Common Subsequence (LCS) problem. 

DP Table Formulation:
* Let dp[i][j] be the length of the LCS of A[1..i] and B[1..j].
* Base case: dp[i][0] = 0 and dp[0][j] = 0.
* Recurrence relation:
    * If A[i] == B[j], then dp[i][j] = dp[i-1][j-1] + 1 (one more letter added to subsequence)
    * If A[i] != B[j], then dp[i][j] = max(dp[i-1][j], dp[i][j-1]).

Final answer: The length of the LCS is LCS = dp[m][n]. The minimum number of operations to transform string A into string B is the sum of characters that need to be deleted from A and those that need to be inserted to form B. The total number of operations is (length(A) - length(LCS)) + (length(B) - length(LCS)).The edit distance is m + n - 2 * LCS.

##### Case 3: All Operations Allowed (Insertion, Deletion, Substitution)
Standard Levenshtein distance problem.

DP Table Formulation:
* Let dp[i][j] be the minimum edit distance between A[1..i] and B[1..j].
* Base case: dp[i][0] = i (delete i characters from A) and dp[0][j] = j (insert j characters to form B).
* Recurrence relation:
    * If A[i] == B[j], then dp[i][j] = dp[i-1][j-1] (no cost, characters match).
    * If A[i] != B[j], we consider three possibilities and take the minimum:
        * Deletion: dp[i-1][j] + 1 (delete A[i]).
        * Insertion: dp[i][j-1] + 1 (insert B[j]).
        * Substitution: dp[i-1][j-1] + 1 (substitute A[i] with B[j]). <br>
        So, dp[i][j] =1(updation/deletion/substitution) + min(dp[i-1][j],dp[i-1][j-1],dp[i][j-1])
Final answer: The minimum edit distance is dp[m][n].

Time: O(N * M), Space: O(N * M)
