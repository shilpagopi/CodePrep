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
