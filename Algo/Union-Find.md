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
