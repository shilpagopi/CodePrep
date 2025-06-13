### Routine Binary Search
```java
    public static int binarySearch(int arr[], int st, int end, int val){
        if(st>end or st==arr.length)
            return -1;
        int mid = (st+end)/2;
        if(arr[mid]==val)
            return mid;
        if(arr[mid]<val)
            return binarySearch(arr,mid+1,end,val);
        return binarySearch(arr,st,mid-1,val);
    }
```

```python
def search(val,l,r):
    while l<=r and l<len(ls):
        m = (l+r)//2
        if ls[m]==val:
            return m
        if val<ls[m]:
            r = m-1
        else:
            l=m+1
    return -1
```

### Find position to insert an element using Binary Search
* Find lesser element with largest index
```python
def pos_to_insert(val,l,r):
    pos = -1
    while l<=r:
        m = (l+r)//2
        if val<ls[m]:
            r = m-1
        else:
            pos = m
            l=m+1
    return pos+1
```

```
    private static int binarySearch(List<Integer> array, int target){
        int position = -1;
        int start = 0, end = array.size()-1;
        while (start <= end) {
            int mid = start + (end - start) / 2;
            if (array.get(mid)>target)
                end = mid - 1;
            else if (array.get(mid)<=target){
                position = mid;
                start = mid + 1;
            }
        }
        return position+1; //+1 for pos of insertion
    }

```
