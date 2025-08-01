# Minimum Spanning Tree
## Kruskal's: 
Builds the MST by adding edges in increasing order of weight, focusing on preventing cycles using Union-Find, till V-1 edges are added. A simple "visited set" that just marks whether a vertex has been "seen" isn't enough because Kruskal's algorithm isn't about traversing the graph from a single starting point. It's about building a forest of trees that eventually merge into a single MST.  
Init: sorted_edges and Union-Find datastructures, mst= []; Until: edges_in_mst == num_vertices - 1
## Prim's: 
Grows the MST from a starting vertex by adding the cheapest edge to a non-MST vertex, focusing on connecting new vertices to the existing MST, till all vertices are connected.
Init: mst = [], min_heap (i.e.,(weight_to_neighbor, v, neighbor_of_v) : v is only utilize to identify full edge in output mst), visited[V]

---

<img width="671" alt="image" src="https://github.com/user-attachments/assets/5db2383f-fedc-43a9-acb6-8053be5a8f53" />  

```python
def kruskal_mst(graph_edges, num_vertices):
    mst = []
    # Sort all edges by their weight in non-decreasing order
    sorted_edges = sorted(graph_edges)
    dsu = DisjointSetUnion(num_vertices)
    edges_in_mst = 0

    for weight, u, v in sorted_edges:
        # If adding this edge does not form a cycle (i.e., u and v are in different sets)
        if dsu.union(u, v):
            mst.append((weight, u, v))
            edges_in_mst += 1
            print(f"  Adding edge ({u}-{v}) with weight {weight}. MST edges: {edges_in_mst}")
            # An MST for a connected graph with V vertices has V-1 edges
            if edges_in_mst == num_vertices - 1:
                break
        else:
            print(f"  Skipping edge ({u}-{v}) with weight {weight} (forms a cycle).")

    if edges_in_mst != num_vertices - 1 and num_vertices > 0:
        print("Warning: Graph is not connected, or num_vertices is incorrect. MST might not include all vertices.")
        if num_vertices == 1 and edges_in_mst == 0:
            print("Graph has only one vertex, MST is empty.")
            return []
        elif num_vertices > 1 and edges_in_mst < num_vertices - 1:
            print(f"Found {edges_in_mst} edges, expected {num_vertices - 1} for a connected graph.")

    return mst
```

<img width="671" alt="image" src="https://github.com/user-attachments/assets/2df3689b-6b7e-4df4-8f4e-03c230c46f04" />  

```python

def prim_mst(graph_adj, num_vertices, start_vertex=0):
    mst_edges = []
    min_heap = []
    in_mst = [False] * num_vertices
    vertices_added = 0

    in_mst[start_vertex] = True
    vertices_added += 1

    # Add all edges connected to the start_vertex to the min_heap
    for neighbor, weight in graph_adj.get(start_vertex, []):
        heapq.heappush(min_heap, (weight, start_vertex, neighbor))

    while min_heap and vertices_added < num_vertices:
        weight, u, v = heapq.heappop(min_heap)
        # If the destination vertex 'v' is already in MST, skip this edge (forms a cycle)
        if in_mst[v]:
            continue
        in_mst[v] = True
        mst_edges.append((weight, u, v))
        vertices_added += 1

        # Add all edges connected to the newly added vertex 'v' to the min_heap,
        # but only if the neighbor is not yet in the MST.
        for neighbor_of_v, weight_to_neighbor in graph_adj.get(v, []):
            if not in_mst[neighbor_of_v]:
                heapq.heappush(min_heap, (weight_to_neighbor, v, neighbor_of_v))

    if vertices_added != num_vertices:
        print("Warning: Graph is not connected, or num_vertices is incorrect. MST might not include all vertices.")
        if num_vertices == 1 and vertices_added == 1:
            print("Graph has only one vertex, MST is empty.")
            return []
        elif num_vertices > 1 and vertices_added < num_vertices:
            print(f"Found {vertices_added} vertices, expected {num_vertices} for a connected graph.")

    return mst
```

