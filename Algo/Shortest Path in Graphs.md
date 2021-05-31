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
Time complexity: O(E.logV) (Derived from  E * pop vertices from minHeap of size |E|: Elog(E) => Elog(V^2) => E.logV)

## Bellman–Ford 
**_Keywords_: Relax all E for |V|-1 times, Shortest path from a single source vertex to all other vertices, Dis[v] array - relax over all E.**

#### Implementation
```
init():
	for each vertex V in G: dis[V] <- infinite
	dis[S] <- 0

for each vertex V in G:			
	for each edge (U,V) in G:
		relax edge(U,V)
		   
relax edge(U,V):
	u = dis[U], v = dis[V], w = edge_weight(U, V)
	if u!= infinite && w!= infinite && u+w<v:
		dis[V]=u+w
```

Check for neg edges:
```
for each edge (U,V) in G:
	relax edge(U,V)
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
