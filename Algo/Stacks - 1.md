# Stacks
* Next Greater Element (First greatest element to right)  
> BruteForce: O(n^2)  
> Store unassigned elements on stack  
> Process every element as if it is a possible greater element  
> Pop all lesser elements from stack  
> Insert curr element to stack as it is unassigned  
> At end, all elements remaining in the stack remain unassigned  
> Time: O(N), Space: O(N)  

* Largest Rectangular Area in a Histogram
> From right to left, compute index of first lesser element  
> Repeat from right to left  
> Traverse again to compute area detererined by right and left boundaries  
