# Graph Connectivity

#### How to check for Strongly connected graph
* Strongly connected means: all vertices should be reachable from every other vertices
* Alternative check: All vertices should be reachable from v and v should be reachable from all vertices (2 DFS traversals)
* Alternative check-2: Check if the graph is 2-edge connected, i.e., no bridges. (single DFS traversal)
* Steps: 
  * DFS from v: check all vertices visited. 
  * If v is reachable from all vertices, then on reversing the edges and doing bfs, all nodes should be visited.
* Brute force: O(V * (V+E)) Alternative: O(V+E)

#### 2-Edge Connectivity
* No bridges present in graph
* For a back edge u —> v, arrival[u] > arrival[v].
```java
 public static int DFS(Graph graph, int v, boolean[] discovered, int[] arrival, int parent, int time)
    {
        arrival[v] = ++time;
        discovered[v] = true;
        int t = arrival[v];
 
        for (int w: graph.adjList.get(v))
        {
            if (!discovered[w]) 
                t = Integer.min(t, DFS(graph, w, discovered, arrival, v, time));
            else if (w != parent)
                t = Integer.min(t, arrival[w]);
        }
 
        // if `v` is not the root node, it is a bridge
        if (t == arrival[v] && parent != -1) {
            System.out.println(parent + ", " + v);
        }
 
        // return the minimum arrival time
        return t;
    }
 ```
