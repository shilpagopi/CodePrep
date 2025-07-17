# Union-Find
```
Initialize parent[V] array with -1 values
Initialize rank[V] array with 0 values

Find(int x){
  if(parent[x]==-1)
    return x;
  parent[x]=Find(parent[x]); // path compression
  return parent[x];
}

Union(x,y){
  parentX = Find(x);
  parentY = Find(y);
  
  //lower rank gets merged with higher rank
  if(rank[parentX]>rank[parentY])
    parent[parentY]=parentX
  else if(rank[parentX]<rank[parentY])
    parent[parentX]=parentY
  else{
     parent[parentX]=parentY;
     rank[parentY]++;
  }
}
```
Time Complexity: α(V): This is the Inverse Ackermann function, which is an extremely slowly growing function and almost a constant in practice. It comes into play due to the optimizations applied in the Union-Find data structure: path compression and union by rank (or size).  
Space Complexity: O(V)
