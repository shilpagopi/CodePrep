# Sorting

#### Stability of Sorting
* A sorting algorithm is said to be stable if two objects with equal or same keys appear in the same order in sorted output as they appear in the input array to be sorted.
* Radix Sort (depends on which algorithm for sub sorting)
* Selection sort is unstable, can be made stable. 

#### Time & Space Complexities
Sorting | Best| Average|Worst|Space|Stable|Remarks
--|--|--|--|--|--|--
Selection Sort|Ω(n^2)|θ(n^2)|O(n^2)|In-place|Can be made stable, but the standard implementation is not.|select the winners|
Bubble Sort|Ω(n)(already sorted)|	θ(n^2)|	O(n^2)| In-place|Stable|bubble up the largest to the end
Insertion Sort|Ω(n)|	θ(n^2)|	O(n^2) |In-place|Stable|first part is sorted|
Heap Sort|	Ω(n log(n))|	θ(n log(n))|	O(n log(n))	 |In-place (if org array is modified)|Unstable
Quick Sort|	Ω(n log(n))|	θ(n log(n))|	O(n^2) (occurs when the pivot selection consistently results in a highly imbalanced partition, e.g., when the array is already sorted)  |In-place, O(logn) to O(n) depending on the implementation and pivot choice (due to recursion stack).|Unstable |partition fn returns partition index
Merge Sort|	Ω(n log(n))|	θ(n log(n))|	O(n log(n))	 |Space: O(n) for temp merging|Stable|divide-and-conquer
Counting Sort|Ω(n+k)|	θ(n+k)|	O(n+k)| k is the range of input|Stable|
Bucket Sort|	Ω(n+k)|	θ(n+k)|	O(n^2)	| Space: O(N+k)|Unstable, but can be made stable if the sorting algorithm used for the buckets is stable.|
Radix Sort||θ(digits * (n+base of decimal system))||Space: O(n+b)|depends on the inner sorting algorithm|


#### Merge Sort
```
   if (l < r) {
        int m = (l + r) / 2;
        mergeSort(arr, l, m);
        mergeSort(arr, m + 1, r);
        merge(arr, l, m, r);
    }
```
```
   def merge_sort(arr):
    if len(arr) > 1:
        mid = len(arr) // 2  # Finding the middle of the array
        L = arr[:mid]  # Dividing the array elements into 2 halves
        R = arr[mid:]

        merge_sort(L)  # Sorting the first half
        merge_sort(R)  # Sorting the second half

        i = j = k = 0

        # Copy data to temp arrays L[] and R[]
        while i < len(L) and j < len(R):
            if L[i] < R[j]:
                arr[k] = L[i]
                i += 1
            else:
                arr[k] = R[j]
                j += 1
            k += 1

        # Checking if any element was left
        while i < len(L):
            arr[k] = L[i]
            i += 1
            k += 1

        while j < len(R):
            arr[k] = R[j]
            j += 1
            k += 1
    return arr
```

#### Selection Sort
Repeatedly selects the smallest element from the unsorted array and swaps it with the first element of the unsorted array.
```
    void SelectionSort(int arr[])
    {
        int n = arr.length;  
        for (int i = 0; i < n-1; i++)
        {
            // Find the minimum element in unsorted array
            int min_idx = i;
            for (int j = i+1; j < n; j++)
                if (arr[j] < arr[min_idx])
                    min_idx = j;
            
            swap(arr,min_idx,i);
        }
    }
```    

#### Bubble Sort
```java
for (int i = 0; i < n-1; i++)
   for (int j = 0; j < n-i-1; j++)
       if (arr[j] > arr[j+1])
           swap(arr[j+1],arr[j]);
 ```
Flag for atleast 1 swap

#### Quick Sort
```java
   private static int partition(int arr[],int l,int r){
       int pivot = arr[r];
       int low = l;   
       for(int j=l;j<r;j++){
           if(arr[j]<pivot){
               swap(arr,low,j);
               low++;
           }
       }
       swap(arr,low,r);
       return low;
   }
   
   public static void quicksort(int arr[],int l,int r){
       if(l<r) {
       int p = partition(arr,l,r);
       quicksort(arr,l,p-1);
       quicksort(arr,p+1,r);
       }
   }
```   

#### Insertion Sort
```java
 for i in range(1, len(arr)): 
     key = arr[i]
     j = i-1
     while j >= 0 and key < arr[j] :
             arr[j + 1] = arr[j]
             j -= 1
     arr[j + 1] = key
```
#### Counting Sort
* Array values are in the range 0 to k; Count in k-length array;
* Print output one by one based on counting array.
```
def counting_sort(arr):
    max_val = max(arr)
    min_val = min(arr)
    range_of_elements = max_val - min_val + 1
    
    count = [0] * range_of_elements
    output = [0] * len(arr)

    # Store count of each character
    for i in range(len(arr)):
        count[arr[i] - min_val] += 1

    # Change count[i] so that count[i] now contains actual position of this element in output array
    for i in range(1, len(count)):
        count[i] += count[i - 1]

    # Build the output array
    for i in range(len(arr) - 1, -1, -1):
        output[count[arr[i] - min_val] - 1] = arr[i]
        count[arr[i] - min_val] -= 1

    # Copy the output array to the input array
    for i in range(len(arr)):
        arr[i] = output[i]
    return arr
```

#### Radix Sort
* Sort(counting sort) by unit digits first, then.. to higher significant digits.
* Time complexity is O(n) to sort an array of integers from 1 to n^c if the numbers are represented in base n
```
    // Do counting sort for every digit. 
    for (int exp = 1; maxNoInArray / exp > 0; exp *= 10)
        countSort(arr, n, exp);
    In countSort, find digit by (arr[i]/exp)%10.         
```
```
def counting_sort_for_radix(arr, exp):
    n = len(arr)
    output = [0] * n
    count = [0] * 10  # For base 10 (digits 0-9)

    for i in range(n):
        index = (arr[i] // exp)
        count[index % 10] += 1

    for i in range(1, 10):
        count[i] += count[i - 1]

    i = n - 1
    while i >= 0:
        index = (arr[i] // exp)
        output[count[index % 10] - 1] = arr[i]
        count[index % 10] -= 1
        i -= 1

    for i in range(n):
        arr[i] = output[i]

def radix_sort(arr):
    max_val = max(arr)
    exp = 1  # Exponent for current digit place
    while max_val // exp > 0:
        counting_sort_for_radix(arr, exp)
        exp *= 10
    return arr
```  

#### Heap Sort
* Parent: (i-1)/2, Child: 2* i+1, 2* i+2
* Heapify: Rearrange i, left, right; If rearranged, recursively call on swapped child.
* Call heapify from n/2 to 0 and build maxHeap
* for i in range(n-1,0): swap heap top with i-th element, reduce heap size by 1, heapify top. 
* Time complexity: O(n log n), Space: O(1)

```
def heapify(arr, n, i):
    largest = i  # Initialize largest as root
    l = 2 * i + 1     # left child
    r = 2 * i + 2     # right child

    # See if left child of root exists and is greater than root
    if l < n and arr[l] > arr[largest]:
        largest = l

    # See if right child of root exists and is greater than root
    if r < n and arr[r] > arr[largest]:
        largest = r

    # Change root, if needed
    if largest != i:
        arr[i], arr[largest] = arr[largest], arr[i]  # swap

        # Heapify the root.
        heapify(arr, n, largest)

def heap_sort(arr):
    n = len(arr)

    # Build a maxheap.
    for i in range(n // 2 - 1, -1, -1):
        heapify(arr, n, i)

    # One by one extract elements
    for i in range(n - 1, 0, -1):
        arr[i], arr[0] = arr[0], arr[i]  # swap
        heapify(arr, i, 0)
    return arr
```
