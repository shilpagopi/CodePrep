# DFS Applications

### Concepts
* Arrival time: time when vertex is explored/visited the first time
* Departure time: time when all eighbours are explored and we are about to backtrack

#### Arrival and Departure Time
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
