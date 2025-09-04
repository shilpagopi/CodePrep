# Arrays

*QuestionPatterns*: Swapping, Index Cycling/Swapping, Index Marking, Sliding Window, Sort and start+end pointers, Cumulative Sum, Replace 0 with -1, Modify from End index to not disturb initial indices, Iterate or search (maybe binary search) in the known bound answer result space (Eg. koko eating bananas leetcode question), Break a chain/circle into array with 2 cases of either ends being absent (eg. in DP questions), Intervals (Sort by start or end time - and think in terms of gantt chart) - use SortedDict from sortedcontainers for binary search

## Sum
#### Sub-Arrays with zero sum
*Question-Pattern* : Cumulative sum, works for integers
* Insert sum 0 at index -1
* Cumulative sum in hashmap. Is any sum repeats, the sub-array in between is zero-sum
* For any non-zero sum, say K, search for sum-K in the hashmap.  

Naive brute force: Time:O(N3),Space:O(1); Most optimized: Time:O(N),Space:O(N)

#### Shortest subarray of positive integers with sum greater than k
*Question-Pattern* : Sliding Window
```python
start = 0
end = 0
while (end < n): 
	while (curr_sum <= k and end < n): # Block to move end ptr
		curr_sum += arr[end] 
		end+= 1
		
	while (curr_sum > x and start < n): # Block to move start ptr
		min_len = Math.min(end - start ,min_len)
		curr_sum -= arr[start] 
		start+= 1
```
Alternate approach for fixed window length: first consider ls[:k] slice, then increment l and r pointers by 1 in a single loop.  
Naive brute force: Time:O(N3),Space:O(1); Most optimized: Time:O(N),Space:O(1)

#### Shortest subarray of integers with sum greater than k

```    # Calculating prefix sums
    for i in range(n):
        pref_sum[i] = A[i] + (pref_sum[i - 1] if i > 0 else 0)
        if pref_sum[i] >= X:
            ans = min(ans, i + 1)  # Updating the answer if the prefix sum is already >= X

    # Looping through the array to find the shortest subarray with sum >= X
    for i in range(n):
        # Removing elements from the front of the deque if the current prefix sum - prefix sum at front >= X
        while dq and pref_sum[i] - pref_sum[dq[0]] >= X: #elements before that will result in longer subarrays
            ans = min(ans, i - dq.popleft())  # Updating the answer
            
        # Removing elements from the back of the deque if the prefix sum at back >= current prefix sum ??
        while dq and pref_sum[dq[-1]] >= pref_sum[i]:
            dq.pop()  # Removing the index from the back

        dq.append(i)  # Adding the current index to the deque

    # If ans is still positive infinity, return -1, else return the length of the shortest subarray
    return -1 if ans == float('inf') else ans
```
Naive brute force: Time:O(N3),Space:O(1); Most optimized: Time:O(N),Space:O(N) (using Prefix Sum and Deque)

#### Triplets in array with given sum
*QuestionPattern* : Sort and start+end pointers
* Sort array, pick each element e, look for Sum-e using two pointers
Brute force: Time:O(N3),Space:O(1); Most optimized: Time:O(N2),Space:O(1)

#### Max Length Subarray with equal number of 0's and 1's
Replace 0 with -1, find max subarray with zero sum.

## Product
#### Max product of two elements
Get Max(L1 * L2, S1 * S2) where L=>largest element, S=>smallest element.

## Re-arrangement
#### Move zeroes to end
*QuestionPattern* : Swapping, Ignore remaining elements
```python
count = 0
for i in range(n): 
	if arr[i] != 0:
		arr[count] = arr[i] 
		count+=1
		
while count < n: 
	arr[count] = 0
	count += 1
```

####  Reverse array
*QuestionPattern* : Swapping
```python
while start < end: 
	A[start], A[end] = A[end], A[start] 
	start += 1
	end -= 1
```

#### Alternate (+) and (-) numbers:
*QuestionPattern* : Swapping
Do quicksort with pivot value 0 and swap
```python
i = -1
for j in range(n): 
	if (arr[j] < 0): 
		i += 1
		arr[i], arr[j] = arr[j], arr[i] 
		
i = 0 if first elem should be positive, else i = 1;
while (arr[i] < 0) and (j < n):
	arr[i], arr[j] = arr[j], arr[i] 
	i += 2     
	j += 1
```

#### Rearrange an array such that arr[i] = i, absent elements are -1:
*QuestionPattern* : Ignore remaining elements, Index Cycling
```python
for i in range(0, len(A)): 
        if (A[i] != -1 and A[i] != i): 
            id = A[i];
			// cyclically accessing indices
            while (A[id] != -1 and A[id] != id):
                newid = A[id]
                A[id] = id
				id = newid
            A[id] = id; 
  
            if (A[i] != i) :
                A[i] = -1; 
```

## Circular Array (wrapping around)
* Use modulo logic: (s[i] - s[i-1] + 26) % 26 (Eg: Refer Group Shifted strings)
