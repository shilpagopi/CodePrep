### Word Break-II
Word Segmentation: check for words to split. Use memoization (valid from index i). Time complexity: O(n.2^n), Space complexity: O(n*2^n)? No need ot use trie, as it will bring addiitonal storage overhead ?

### Super Washing Machines
The minimum number of moves to equalize the number of dresses in each washing machine. Can move dresses only to nearby machines (dummy constraint). 
convert array into arr[i]-avg. Take max(abs(cumulative_sum)).

### Sliding Window Maximum
Given an array of n integer with duplicate number, and a moving window(size k), move the window at each iteration from the start of the array, find the maximum number inside the window at each moving.
Maintain a Monotonically Decreasing Deque of Indices: The deque stores the indices of the elements within the current window in decreasing order of their values in nums. The index at the front of the deque always corresponds to the maximum element in the current window.
Iterate Through the Array: The following operations are performed at each step while iterating through the array nums using an index i:
Remove Out-of-Bounds Indices from the front of the queue.
Remove Smaller Elements: While the deque is not empty and the current element nums[i] is greater than or equal to the element at the back of the deque (nums[q[-1]]), pop elements from the back. These smaller elements are no longer relevant for determining the maximum in future windows.
Time Complexity : O(n), Space complexity: O(k)

### Split Array sum
Question: Splitting an array nums into k non-empty, contiguous subarrays to minimize the largest sum among them
<img width="671" alt="image" src="https://github.com/user-attachments/assets/7a0ce1b5-81ca-4b2b-a5c8-4240338048a2" />
Time complexity: O(n log(Sum - Maxelement)); Space complexity is O(1). 

### Minimize Malware Spread
Return the node that if removed, would minimize. Do Union-Find tracking size of connected components. Count initial affected node list and count no of infected nodes in each component. (if there are no two nodes, this component cannot be saved). 

<img width="671" alt="image" src="https://github.com/user-attachments/assets/a4a15d7b-bd61-41a3-b128-130acf4b3833" />


