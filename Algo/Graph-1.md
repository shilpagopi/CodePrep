# Graph - 1 
A Graph is a non-linear data structure consisting of nodes and edges.

### Representations
1. Adjacency Matrix : Space: O(V^2), Time: Edge accessing O(1)
2. Adjacency List   : Space: O(V+E), worst case: O(V^2), Time - O(E)

### BFS and DFS
**_Keywords_: BFS - Queue, DFS - Stack, Visited**

#### Implementation
```
- create queue for BFS and stack for DFS.
- mark start node visited and add to queue/stack
- in loop over queue/stack:
	- pop from queue/stack. print.
	- for all its adjacent nodes:
          - if not visited:
	    - mark visited and add to queue/stack
```
Time: O(V+E)	
For disconnected graphs, check visited array in a wrapper loop

### Topological Sorting

**_Keywords_: Dependencies, Stack**

Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for every directed edge uv, vertex u comes before v in the ordering.
#### Implementation
In topological sorting, we use a temporary stack. We don’t print the vertex immediately, we first recursively call topological sorting for all its adjacent vertices, then push it to a stack. Finally, print contents of stack.			
```
- loop thru vertices:
  - mark v as visited and call topologicalSort(v)
  
- topologicalSort(v)
  - for all its adjacent nodes:
      - if not visited:
	    - call TopologicalSort()
  - push to stack
  
- print stack
```
Time: O(V+E)
