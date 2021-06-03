# Arrays

*QuestionPatterns*: Swapping, Index Cycling/Swapping, Index Marking, Sliding Window, Sort and start+end pointers, Cumulative Sum, Replace 0 with -1

## Sum
#### Sub-Arrays with zero sum
*Question-Pattern* : Cumulative sum, works for integers
* Insert sum 0 at index -1
* Cumulative sum in hashmap. Is any sum repeats, the sub-array in between is zero-sum  
For any non-zero sum, say K, search for sum-K in the hashmap.

#### Shortest subarray with sum greater than k
*Question-Pattern* : Sliding Window
```python
start = 0
end = 0
while (end < n): 
	while (curr_sum <= k and end < n): 
		curr_sum += arr[end] 
		end+= 1
		
	while (curr_sum > x and start < n): 
		min_len = Math.min(end - start ,min_len)
		curr_sum -= arr[start] 
		start+= 1
```
#### Triplets in array with given sum
*QuestionPattern* : Sort and start+end pointers
* Sort array, pick each element e, look for Sum-e using two pointers

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
