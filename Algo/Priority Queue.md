# Priority Queue

#### Find the smallest range with at least one element from each of the given sorted lists
[ 3, 6, 8, 10, 15 ], [ 1, 5, 12 ], [ 4, 8, 15, 16 ] Ans. 4-6
* Maintain min-heap of smallest elements being considered in each list
* Pop smallest and add next element in the same list
* Maintain max element present in the heap and range is diff between min and max 
