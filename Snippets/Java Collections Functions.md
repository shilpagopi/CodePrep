# Java Collections Functions
### ArrayList
ls.add()  
ls.add(index,element)  
ls.get(index)  
ls.contains(element)  
ls.remove(element)  
ls.remove(index)  
ls.indexOf(element) - first element  
ls.lastIndexOf(element)  
ls.size()  
ls.clear()  
ls.remove(index)  

##### Implementation details:
* Resizable array:grows and shrinks
* Ordered collection;maintains insertion order
* Not primitive types, only boxed types
* Not synchronized

### LinkedList
ls.addFirst(element)  
ls.addLast(element)  
ls.peek() retrieves head without removal  
ls.remove() retrieves and removes head  

##### Implementation details:
* Non contiguous

### Hashmap
mp.containsKey(key)  
mp.containsValue(val)  

### LinkedHashMap: 
##### Implementation details:
* Doubly linked list
* LRU cache

### TreeMap 
tr.firstKey()  
tr.lastKey()  
##### Implementation details:
* Red-Black Trees
