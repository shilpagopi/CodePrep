# Graph - 1 
A Graph is a non-linear data structure consisting of nodes and edges.

#### Specification questions: Directed? Cyclic? Weighted? Connected? Input format?

### Representations
1. Adjacency Matrix : Space: O(V^2), Time: Edge accessing O(1)
2. Adjacency List   : Space: O(V+E), worst case: O(V^2), Time - O(E)

### Types
* Undirected: Max E = V×(V-1)/2 (not valid for multigraph)
	* Multiple graph (Multigraph): More than 1 undirected edge between two V allowed
	* Simple graph (no loops? and no multilple edges between two V)
* Directed graph (Digraph): Max E = V*(V-1) -> cyclic, acyclic(DAG)
* Weighted/unweighted graph
* Complete graph: All vertices are adjacent to each other. Maximum edges are present. E = V*(V-1)
* Connected graph: No disconnected components: min E = V-1.
* Connected graph w/o cycles: Tree
* Graph without cycles: Forest
* Strongly connected: every vertex is reachable from every other vertex
E can vary from O(1) to O(V^2)

### Types of Edges
* Tree edge (parent-child)/Forward edge (ancestor to child): arrival[u] < arrival[v], departure[u] > departure[v]
* Backedge (child to ancestor: opp of forward edge): arrival[u] > arrival[v], departure[u] < departure[v]
* Cross edge (node to non-ancestor): arrival[u] > arrival[v], departure[u] > departure[v] (Reach cousin? first, leave cousin first)

* departure[u] < departure[v]: only for backedge
* If arrival[u] > arrival[v], (reaching an already seen node), it can either be a cross edge (if v present in stack, yet to be explored) or a back edge (v not present in stack, already been explored)

### BFS and DFS
**_Keywords_: BFS - Queue, DFS - Stack, Visited**

#### Iterative Implementation
```
- create queue for BFS and stack for DFS.
- mark start node visited and add to queue/stack
- in loop over queue/stack:
	- pop from queue/stack. print. 
	- for all its adjacent nodes:
          - if not visited:
	    - mark visited and add to queue/stack (call DFS recursively here inorder to not load up the stack space with the entire tree)
```
Time: O(V+E)  
O(V+|E|) for directed and O(V+2|E|) for undirected  
For disconnected graphs, check visited array in a wrapper loop  
Memory: BFS: O(b^d), DFS: O(bh), where b: branching factor, d: at distance d from root, h: height

#### Recursive Implementation
```
- mark start node visited and call DFS(start,visited)
- DFS(node,visited):
	- print node
	- for all its adjacent nodes:
          - if not visited:
	    - mark visited and DFS(adj,visited)
```
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
