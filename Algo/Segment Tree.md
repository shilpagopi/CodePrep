# Segment Tree
* a[0...(n-1)]
* tree[1...n]; tree can have atmost 4n nodes
* kids of node v: 2*v, 2*v+1
* parent of node v: v//2
* parent node index: [tl, tr], kids: [tl,tm], [tm+1, tr] where tm = (tl+tr)//2

### Generic Recursive structure for Construction/Updation/Querying
basic_args: v, tl, tr \
extra_args:
* querying: query range (l,r)
* construction: base array a[]
* updation: update_pos, new_val
  
```python
def fun(v:tree_node_index, tl:tree_left, tr:tree_right, <extra_args>){
    if query_right<query_left:                        #in querying
        do pruning and return default value

    if tl==tr (#in construction/updation), or tl==l and tr==r (#in querying):    
        operate on tree[v]

    else:
        find mid, tm = (tl+tr)//2

        # process left, process right for update/construct, only process either one based on if (pos <= tm)
        left = fun(v*2, tl, tm, <extra_args>);
        right = fun(v*2+1, tm+1, tr, <extra_args>);

        return merge(left,right) #during construction no return, directly merge(tree[2*v],tree[2*v+1])
}
```        

### Construction
```python
def build(v, tl, tr, a) {
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
    left_out = sum(v*2, tl, tm, l, min(r, tm))
    right_out = sum(v*2+1, tm+1, tr, max(l, tm+1), r)  
    return  left_out + right_out ;
}
```
### Update
```python
void update(v, tl, tr, int pos, int new_val) {
    if (tl == tr) {
        t[v] = new_val;
    } else {
        int tm = (tl + tr) / 2;
        if (pos <= tm)
            update(v*2, tl, tm, pos, new_val);
        else
            update(v*2+1, tm+1, tr, pos, new_val);
        t[v] = t[v*2] + t[v*2+1];
    }
}
```


