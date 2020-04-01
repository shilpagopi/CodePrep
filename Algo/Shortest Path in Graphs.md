# Shortest Path in Graphs 

## Dijkstra's

**_Keywords_: Greedy, Priority Heap, Shortest path from a single source vertex to all other vertices**

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
Time complexity: O(V LogV)

## Bellman–Ford 
**_Keywords_: Relax all E for |V|-1 times, Shortest path from a single source vertex to all other vertices**

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
