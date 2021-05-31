# Graph Connectivity

#### How to check for Strongly connected graph
* Strongly connected means: all vertices should be reachable from every other vertices
* Alternative check: All vertices should be reachable from v and v should be reachable from all vertices
* Steps: 
  * DFS from v: check all vertices visited. 
  * If v is reachable from all vertices, then on reversing the edges and doing bfs, all nodes should be visited.
* Brute force: O(V * (V+E)) Alternative: O(V+E)
