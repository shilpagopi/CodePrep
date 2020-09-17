# Java Collections Functions
### ArrayList
alist.add()  
alist.add(index,element)  
alist.get(index)  
alist.contains(element)  
alist.remove(element)  
alist.remove(index)  
alist.indexOf(element) - first element  
alist.lastIndexOf(element)  
alist.size()  
alist.clear()  

##### Implementation details:
* Resizable array:grows and shrinks
* Ordered collection;maintains insertion order
* Not primitive types, only boxed types
* Not synchronized

### LinkedList
LinkedList<String> ls = new LinkedList<String>()  
ls.addFirst(element) or ls.add()  
ls.addLast(element)    
  
ls.set(index, element)  
ls.add(index,element)   
  
ls.peek() //retrieves head without removal    
ls.get(index)  
ls.indexOf(element)  
ls.lastIndexOf(element)  
ls.contains(element)  

ls.remove() or ls.removeFirst(); //retrieves and removes head  
ls.removeLast()  
ls.remove(index)  

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
