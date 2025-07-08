# Matrix
* rotate 90 degrees: for each pos(i,j) along top horizontal side of the matrix (except end corner), get rotated pos: [(j,n-i),(n-i, n-j),(n-j,i)].
* For fill colour problem, if checking coloured by two parties, follow 1,2 enums or binary encoding.

* Distinct islands with rotation and reflection: Sort each representation and normalize it setting first cell as (0,0).  
Reflection: (x,-y), Rotations: (x,y), (-y,x), (-x,-y), (y,-x) + rottaions of reflections. (8 combinations)  
Time Complexity: O(m * n log (m * n)) (=Sorting all coordinates of each island), Space complexity: O(m*n) (=max size of island)
