# Sorting
* A sorting algorithm is said to be stable if two objects with equal or same keys appear in the same order in sorted output as they appear in the input array to be sorted.

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
Radix Sort|	Ω(nk)|	θ(nk)|	O(nk)

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
