# Matrix
* rotate 90 degrees: for each pos(i,j) along top horizontal side of the matrix (except end corner), get rotated pos: [(j,n-i),(n-i, n-j),(n-j,i)].
* For fill colour problem, if checking coloured by two parties, follow 1,2 enums or binary encoding.

* Distinct islands with rotation and reflection: Sort each representation and normalize it setting first cell as (0,0).  
Reflection: (x,-y), Rotations: (x,y), (-y,x), (-x,-y), (y,-x) + rottaions of reflections. (8 combinations)  
Time Complexity: O(m * n log (m * n)) (=Sorting all coordinates of each island), Space complexity: O(m*n) (=max size of island)

## BFS in Matrix
*Question-Pattern**: BFS in Matrix
* Add all sources to queue. Store all state variables (eg, cost,r,c) in the queue entry.
* After popping from queue: check termination condition
* Take directions as a list
* Mark visited in matrix to avoid cycles or store cost in the cells
* If cost of different directions vary, add the nil cost to from of the queue and higher costs to end of queue.

Sample code:
```python
def shortestPathBinaryMatrix(self, grid: list[list[int]]) -> int:
      n = len(grid)

      if grid[0][0] == 1 or grid[n-1][n-1] == 1:
          return -1
      
      queue = collections.deque([(0, 0, 1)])  # (row, col, path_length)
      grid[0][0] = 1
      directions = [(-1, 0),(0, -1), (0, 1),(1, 0)]
      
      while queue:
          r, c, length = queue.popleft()

          if r == n - 1 and c == n - 1:
              return length
          
          for dr, dc in directions:
              nr, nc = r + dr, c + dc
              
              # Check for valid neighbors
              if 0 <= nr < n and 0 <= nc < n and grid[nr][nc] == 0:
                  grid[nr][nc] = 1 # Mark as visited
                  queue.append((nr, nc, length + 1))
      
      return -1
```
