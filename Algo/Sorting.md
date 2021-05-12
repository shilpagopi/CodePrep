# Sorting

#### Stability of Sorting
* A sorting algorithm is said to be stable if two objects with equal or same keys appear in the same order in sorted output as they appear in the input array to be sorted.
* QuickSort and HeapSort are unstable (can be made stable)
* Bubble Sort, Insertion Sort, Merge Sort, Count Sort, Radix Sort (depends on which algorithm for sub sorting)

#### Time Complexities
Sorting | Best| Average|Worst
--|--|--|--|
Selection Sort|Ω(n^2)|θ(n^2)|O(n^2)	 
Bubble Sort|Ω(n)|	θ(n^2)|	O(n^2)	 
Insertion Sort|Ω(n)|	θ(n^2)|	O(n^2)	 
Heap Sort|	Ω(n log(n))|	θ(n log(n))|	O(n log(n))	 
Quick Sort|	Ω(n log(n))|	θ(n log(n))|	O(n^2)	 
Merge Sort|	Ω(n log(n))|	θ(n log(n))|	O(n log(n))	 
Bucket Sort|	Ω(n+k)|	θ(n+k)|	O(n^2)	 
Radix Sort||θ(digits * (n+base of decimal system))|	
Counting Sort|Ω(n+k)|	θ(n+k)|	O(n+k)

#### Selection Sort
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
  
            swap(arr,mind_idx,i);
        }
    }
```    

#### Counting Sort
* Array values are in the range 0 to k; Count in k-length array;
* Print output one by one based on counting array.  

#### Radix Sort
* Sort(counting sort) by unit digits first, then.. to higher significant digits.
* Time complexity is O(n) to sort an array of integers from 1 to n^c if the numbers are represented in base n
```
    // Do counting sort for every digit. 
    for (int exp = 1; maxNoInArray / exp > 0; exp *= 10)
        countSort(arr, n, exp);
    In countSort, find digit by (arr[i]/exp)%10.         
```        
