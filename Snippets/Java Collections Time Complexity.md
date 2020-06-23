# Java Collections Time Complexity
### ArrayList
add() – O(1)  
get(index) – O(1)  
add(index, element) – O(n)  
remove() – O(n)  
contains() – O(n)  
indexOf() – O(n)  

### Linkedlist (internally doubly linked list)  
All O(n) except add() – O(1)   

### Hash - All O(1)  
HashMap, LinkedHashMap,IdentityHashMap,WeakHashMap,EnumMap,ConcurrentHashMap  
HashSet, LinkedHashSet, EnumSet have internal HashMap implementation  

### Tree - All O(log n)  
TreeMap, TreeSet (has internal TreeMap implementn)  

### ConcurrentSkipListMap - All O(log n)  
