# Graph - 1 
A Graph is a non-linear data structure consisting of nodes and edges. \
Trackers: seen[], explored[], parent_node (how did I reach the current vertex), adj_vertices, timings of seeing and exploration, BFS (distance from root node), DFS (computation from all subgraph)

#### Specification questions: Directed? Cyclic? Weighted? Connected? Input format?
#### What do we know? Curr_node, Adj, Parent/Predecessor node, Curr_time, Exit time, Explored nodes, Seen nodes, Cost

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
	    - mark visited and add to queue/stack (call DFS recursively here inorder to not load up the stack space with the entire graph)
```

```
# DFS
visited = set()
visited.add(start_node)

def dfs(graph, start_node, visited):
    print(start_node) 

    for neighbor in graph.get(start_node, []):
        if neighbor not in visited:
            visited.add(neighbor)
            **dfs(graph, neighbor, visited)**

# BFS
visited = set()
visited.add(start_node)

queue = deque()
queue.append(start_node)

def bfs(graph, start_node):
    while queue:
        current_node = queue.popleft()
        print(current_node)  # Print the visited node

        # Explore neighbors of the current node
        for neighbor in graph.get(current_node, []):
            if neighbor not in visited:
                visited.add(neighbor)
                **queue.append(neighbor)**
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
        - do any rootnode computation post all dfs exploration of subgraph
```
Variants:
QuestionPattern: BFS with state tracking: put all state variables in queue and visited. refer shortest path with Max k obstacle removal.


### Topological Sorting

**_Keywords_: Dependencies, Stack**

Topological sorting for Directed Acyclic Graph (DAG) is a linear ordering of vertices such that for every directed edge uv, vertex u comes before v in the ordering.
#### DFS Implementation
In topological sorting, we use a temporary stack. We don’t print the vertex immediately, we first recursively call topological sorting for all its adjacent vertices, then push it to a stack. Finally, print contents of stack.			
```
- loop thru vertices:
  - mark src as visited and call topologicalSort(src)
  
- topologicalSort(v)
  - for all its adjacent nodes:
      - if not visited:
        - mark adj as visited
	    - call TopologicalSort()
  - push to stack #Design: Post compute after DFS
  
- print stack
```
Time: O(V+E)

#### Kahn's algorithm
If cycles are present, then topological sort will not be able to cover all vertices.
```python
    queue = deque([u for u in in_degree if in_degree[u] == 0])

    topological_order = []
    while queue:
        u = queue.popleft()
        topological_order.append(u)

        # Decrease in-degree of adjacent vertices and add to queue if their in-degree becomes 0
        for v in adj[u]:
            in_degree[v] -= 1
            if in_degree[v] == 0:
                queue.append(v)

    # Check for cycles
    if len(topological_order) == len(in_degree):
        return topological_order
    else:
        # A cycle exists, as not all vertices were included in the sort
        return []
```
Time: O(V+E), Space: O(V)


