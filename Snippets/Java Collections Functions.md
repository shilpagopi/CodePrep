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
ls.addFirst(element) 
ls.addLast(element) or ls.add()    
  
ls.set(index, element)  // Resets earlier value at given index, invalid for index = ls.size()
ls.add(index,element)   // Add works as insertion of new node, is valid for index = ls.size()
  
ls.peek() //retrieves head without removal    
ls.get(index)  
ls.indexOf(element)  
ls.lastIndexOf(element)  
ls.contains(element)  

ls.remove() or ls.removeFirst(); //retrieves and removes head  
ls.removeLast()  
ls.remove(index)  
arr.removeFirstOccurrence(element);
arr.removeLastOccurrence(element);

##### Implementation details:
* Non contiguous

### Hashmap
mp.containsKey(key)  
mp.containsValue(val)  
mp.replace(key,newValue); //blind replacement
mp.replace(key,oldValue,newValue); //replaces only if oldValue matches

### LinkedHashMap: 
##### Implementation details:
* Doubly linked list
* LRU cache

### TreeMap 
tr.firstKey()  
tr.lastKey()  
tr.firstEntry().getValue()
tr.containsKey(key) or tr.containsValue(value)
tr.pollFirstEntry() or tr.pollLastEntry()
tr.higherKey(key)
tr.lowerKey(key)
tr.replace(key,newValue); //blind replacement
tr.replace(key,oldValue,newValue); //replaces only if oldValue matches

##### Implementation details:
* Red-Black Trees

### TreeSet
arr.first()
arr.last()
arr.higher(element) // returns next higher element
arr.lower(element) 

arr.add(element)
arr.remove(element)
arr.contains(element)

##### Implementation details:
* Internally uses TreeMap
