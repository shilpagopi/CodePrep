# Stacks and Queues
*QuestionPattern*: Stacks can be used to keep track of next greater/lesser element on either sides.
*QuestionPattern*: For maintaining a fixed window, use a queue. Envision as a stack with bottom modifiable. At each new element in array, discard from bottom potential elements in out of window bounds. (Eg.Sliding Window Min/Max problem)

#### Next Greater Element (First greatest element to right)  
> BruteForce: O(n^2)  
> Store unassigned elements on stack  
> Process every element as if it is a possible greater element  
> Pop all lesser elements from stack  
> Insert curr element to stack as it is unassigned  
> At end, all elements remaining in the stack remain unassigned  
> Time: O(N), Space: O(N)  

#### Largest Rectangular Area in a Histogram
> From right to left, compute index of first lesser element  
> Repeat from right to left  
> Traverse again to compute area detererined by right and left boundaries
> Logic: For every bar, we consider the largest possible rectangle that uses that bar as its minimum height. The left[i] and right[i] indices define the maximum possible width for a rectangle of height heights[i] because any wider rectangle would have to include a bar shorter than heights[i], which would then limit its height.

#### Longest balanced parenthesis in a string
* Use stack to traverse through the string like parenthesis balancing; Add -1 index to stack at beginning.
* Alternative: use +/-1 and store in hashmap the first index at which cumulative sum is found
* Time complexity: O(n), Space: O(n)
