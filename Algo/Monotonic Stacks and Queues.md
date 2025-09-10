# Monotonic Stacks and Queues
### Next Greater Element
**Question-Pattern**: Monotonic stack. Hint: Keep unassigned values in the stack.
```python
  for i in range(n):
      # While the stack is not empty and the element at the top of the stack
      # is less than the current element, pop from the stack.
      # The current element is the NGE for the popped element.
      while stack and arr[stack[-1]] < arr[i]:
          result[stack.pop()] = arr[i]
      
      # Push the current element's index onto the stack
      stack.append(i)
  
  return result
```
