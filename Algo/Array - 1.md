# Arrays
## Re-arrangement
##### Move zeroes to end
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
#####  Reverse array
*QuestionPattern* : Swapping
```python
while start < end: 
	A[start], A[end] = A[end], A[start] 
	start += 1
	end -= 1
```

##### Shortest subarray with sum greater than k
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
