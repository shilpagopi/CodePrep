# Segment Tree
* a[0...(n-1)]
* tree[1...n]; tree can have atmost 4n nodes
* kids of node v: 2*v, 2*v+1
* parent of node v: v//2
* parent node index: [tl, tr], kids: [tl,tm], [tm+1, tr] where tm = (tl+tr)//2

### Construction
```python
def build(a, v, tl, tr) {
    if (tl == tr) {
        t[v] = oper(a[tl]); #after recursion, tl will fall in corrected index v
    } else {
        int tm = (tl + tr) / 2;
        build(a, v*2, tl, tm);
        build(a, v*2+1, tm+1, tr);
        t[v] = oper(t[v*2],t[v*2+1]);
    }
}
```
### Querying
```python
def sum(v,tl, tr, l, r) {
    if (l > r) 
        return 0; # Modify default value as per tree nature
    if (l == tl && r == tr) {
        return t[v];
    }
    int tm = (tl + tr) / 2;
    # break down query range, modify query parameters, not tree traversal parameters
    return sum(v*2, tl, tm, l, min(r, tm) + sum(v*2+1, tm+1, tr, max(l, tm+1), r);
}
```


