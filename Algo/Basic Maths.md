# Basic Maths
#### GCD or HCF
```java
static int gcd(int a, int b)
{
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

    findPowerSet(S, set, n - 1); //skip this element
}
````    
