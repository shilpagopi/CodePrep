# Graph - 2

### DFS Concepts
* Arrival time: time when vertex is explored/visited the first time
* Departure time: time when all eighbours are explored and we are about to backtrack
* DP/Memoization in DFS: While going over adjacent nodes, store state in local temp variable/flag and mark final state at the end of exploring all adjacent nodes. Do all computation at root node after exploring all adj nodes.
* If cycles are encountered, use seen and explored arrays and return/break out of process on encountering an adj node with seen=True, but explored = False.

#### Arrival and Departure Time
*QuestionPattern*: DFS returns non-void datatype
``` java
    public static int DFS(Graph graph, int v, boolean[] discovered, int[] arrival, int[] departure, int time)
    {        
        arrival[v] = ++time;
        for (int i: graph.adjList.get(v))
        {
            if (!discovered[i]) {
                discovered[i] = true;
                time = DFS(graph, i, discovered, arrival, departure, time);
            }
        }
        departure[v] = ++time; 
        return time;
    }
```    
#### Bipartite Graph Check
*QuestionPattern*: DFS returns non-void datatype
Bipartite: Graph can be divided into two disjoint sets with no intra-set edge  
Can be checked by 2-coloring or does not contain any odd cycle  
``` java
    public static int DFS(Graph graph, int v, boolean[] discovered, int[] color)
    {        
        for (int i: graph.adjList.get(v))
        {
            if (!discovered[i]) {
                discovered[i] = true;
                color[i]=!color[v];
                if(!DFS(graph, i, discovered, color)
                    return false;
            }
            else if (color[v] == color[i]) {
                return false;
            }
        }
        return true;
    }
```    

#### Check for cycles in undirected graph
*QuestionPattern*: Pass parent indicator, DFS returns non-void datatype, no backedge other than parent
``` java
    public static int isAcyclicDFS(Graph graph, int v, boolean[] discovered, int parent)
    {        
        for (int i: graph.adjList.get(v))
        {
            if (!discovered[i]) {
                discovered[i] = true;
                if(!isAcyclicDFS(graph, i, discovered, v)
                    return false;
            }
            else if (i != parent) {
                return false;
            }
        }
        return true;
    }
``` 
#### Check for cycles in undirected graph using Union-Find
*QuestionPattern*: Union-Find initialize parent with Vi value

```java
        // Iterate for every edge (u, v)
        for (int u = 1; u <= N; u++)
        {
            // Recur for all adjacent vertices
            for (int v: graph.adjList.get(u))
            {
                int x = UnionFind.FindParent(u);
                int y = UnionFind.FindParent(v);
                if (x == y) 
                    return true; //same parent => cycle  
                else 
                    UnionFind.Union(x, y);     
            }
        }
```

#### Check for cycles in directed graph (isDAG)
*QuestionPattern*: Track ancestors in boolean array (sequence does not matter), DFS returns non-coid datatype
* Back edge to parent or ancestor is a cycle. Edge to a previously visited node need not be a cycle.
``` java
    public static int isAcyclicDFS(Graph graph, int v, boolean[] discovered, boolean[] isAncestor)
    {        
        isAncestor[v]=true;
        for (int i: graph.adjList.get(v))
        {
            if (!discovered[i]) {
                discovered[i] = true;
                if(!isAcyclicDFS(graph, i, discovered, isAncestor)
                    return false;
            }
            else if (isAncestor[i]) { //backedge to ancestor
                return false;
            }
        }
        isAncestor[v]=false;
        return true;
    }
``` 
#### Check for cycles in directed graph (isDAG)
```java
    // DO DFS, check for backedges
    for (int u = 0; u < N; u++)
    {
        for (int v: graph.adjList[u])
        {
            if (departure[u] <= departure[v]) { //equality for self loop
                return false;
            }
        }
    }
```

#### Trimming leaf nodes like Topological Sort
*QuestionPattern*: Trimming leaf nodes \
Find root nodes of minimum height trees (MHTs) in an undirected graph without simple cycles \
Trim leaf nodes like topological sort. The remaining one or two nodes are possible root nodes.
