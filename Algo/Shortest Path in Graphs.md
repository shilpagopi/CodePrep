# Shortest Path in Graphs 

## Dijkstra's

**_Keywords_: Greedy, Priority Heap, Shortest path from a single source vertex to all other vertices, Go to nearest vertex and mark it covered**

#### Implementation
```
init():
	for each vertex V in G: 
		dis[V] <- infinite
		processed[V]=false
	dis[S] <- 0
	
Loop over Priority Heap(P) for all V:
  Pop U from P, Mark U as processed
  For all adjacent vertices V, 
    if unprocessed, relax edge(U,V)
  	
relax edge(U,V):
	u = dis[U], v = dis[V], w = edge_weight(U, V)
	if u!= infinite && w!= infinite && u+w<v:
		dis[V]=u+w

```

```python
class Graph:
   def __init__(self, graph: dict = {}):
       self.graph = graph  # A dictionary for the adjacency list

   def add_edge(self, node1, node2, weight):
       if node1 not in self.graph:  # Check if the node is already added
           self.graph[node1] = {}  # If not, create the node
       self.graph[node1][node2] = weight  # Else, add a connection to its neighbor

   def shortest_distances(self, source: str):
       # Initialize the values of all nodes with infinity
       distances = {node: float("inf") for node in self.graph}
       distances[source] = 0  # Set the source value to 0

       # Initialize a priority queue
       pq = [(0, source)]
       heapify(pq)

       # Create a set to hold visited nodes
       visited = set()

       while pq:  # While the priority queue isn't empty
           current_distance, current_node = heappop(
               pq
           )  # Get the node with the min distance

           if current_node in visited:
               continue  # Skip already visited nodes, also do not reprocess redundant longer distances stored in the heap

           visited.add(current_node)  # Else, add the node to visited set

           for neighbor, weight in self.graph[current_node].items():
	       # Calculate the distance from current_node to the neighbor
	       tentative_distance = current_distance + weight
	       if tentative_distance < distances[neighbor]:
	           distances[neighbor] = tentative_distance
	           heappush(pq, (tentative_distance, neighbor))
	
	return distances
```

###### Print shortest path
```python
def get_predecessors(self, distances):
	predecessors = {node: None for node in self.graph}
	
	for node, distance in distances.items():
	   for neighbor, weight in self.graph[node].items():
	       if distances[neighbor] == distance + weight:
		   predecessors[neighbor] = node

return predecessors

def shortest_path(self, source: str, target: str):
   predecessors = self.get_predecessors(distances)

   path = []
   current_node = target

   # Backtrack from the target node using predecessors
   while current_node:
       path.append(current_node)
       current_node = predecessors[current_node]

   # Reverse the path and return it
   path.reverse()

   return path
```

Time complexity: O(E.logV) (Derived from  E * pop vertices from minHeap of size |E|: Elog(E) => Elog(V^2) => E.logV)

## Bellman–Ford 
**_Keywords_: Relax all E for |V|-1 times, Shortest path from a single source vertex to all other vertices, Dis[v] array - relax over all E.**
Unlike the Dijkstra algorithm, the Bellman-Ford algorithm can handle negative edge weights, and it can also detect negative weight cycles.
Intuititon?: The maximum length shortest path from u to v could only be the one passing through all other vertices, i.e, V-1 edges. 

#### Implementation
```
init():
	for each vertex V in G: dis[V] <- infinite
	dis[S] <- 0
        predecessors[V]=[None]*V

for i in range(self.V-1):		
	for each edge (U,V) in G:
		relax edge(U,V)
		   
relax edge(U,V):
	u = dis[U], v = dis[V], w = edge_weight(U, V)
	if u!= infinite && w!= infinite && u+w<v:
		dis[V]=u+w
                predecessors[v] = u

```

Check for neg edges:
```
for each edge (U,V) in G:
	relaxed_flag = relax edge(U,V)
	if relaxed_flag:
		print("Negative cycles detected")
```
		
Time complexity: O(V.E)

## Floyd Warshall

**_Keywords_: 3 loops over V, All sources to all other vertices, dis[u][v] matrix with k intermediate vertices**

#### Implementation
```
init():	 
	for each edges G:  dis[U][V] <- weight[U][V]
	for each vertex V in G:  dis[V][V] =0

for (int k = 0; k < V; k++)
	for (int u = 0; u < V; v++)
		for (int v = 0; v < V; u++) 
			relax edge(u,v,k)			
		   
relax edge(u,v,k):
	 uv = edge_weight(U, V), uk = edge_weight(U,K), kv = edge_weight(K,V)
	 if uk!= infinite && kv!= infinite && uk+kv<uv:
		uv = uk + kw
```

Check for neg edges:
```
for each vertex V in G:
	check dis[V][V] < 0
``` 
		
Time complexity: O(V^3)

Space complexity: O(V^2)

### BFS 
Use for shortest path from single src to single dest.
