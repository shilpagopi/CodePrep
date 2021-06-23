# Basic Maths
#### GCD or HCF
```java
static int gcd(int a, int b)
{   // 5 conditions
    if (a == 0)
      return b;
    if (b == 0)
      return a;

    if (a == b)
        return a;

    if (a > b)
        return gcd(a-b, b);
    return gcd(a, b-a);
}
```

#### Generate PowerSet
```java
//Sort S if numbers are duplicated.  
public static void findPowerSet(int[] S, Deque<Integer> set, int n)
{
    if (n == 0)
    {
        System.out.println(set);
        return;
    }

    set.addLast(S[n - 1]); //consider this element
    findPowerSet(S, set, n - 1);
    set.removeLast();     // backtrack

    // remove adjacent duplicate elements
    while (n > 0 && S[n] == S[n - 1]) 
        n--;

    findPowerSet(S, set, n - 1); //skip this element
}
````    
> Alternative approach: Consider binary representation of numbers till 2^n -1 and add elements corresponding to bits set, store outputs in HashSet
