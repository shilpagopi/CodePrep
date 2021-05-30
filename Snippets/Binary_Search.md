### Routine Binary Search
```java
    public static int binarySearch(int arr[], int st, int end, int val){
        if(st>end)
            return -1;
        int mid = (st+end)/2;
        if(arr[mid]==val)
            return mid;
        if(arr[mid]<val)
            return binarySearch(arr,mid+1,end,val);
        return binarySearch(arr,st,mid-1,val);
    }
```

### Find position to insert an element using Binary Search
* Find lesser element with largest index
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
