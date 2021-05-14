# Java Collections Functions

### Functions
Functionality | ArrayList | LinkedList | HashMap | TreeMap | TreeSet |
--|--|--|--|--|--|
**Insertion**|
Insert| --| --| map.**put**(k,v)|tmap.put(k,v)|treeset.add(v)|
Insert at Start | -- | ll.**addFirst**(v)| --|--|--|
Insert at End | alist.add() | ll.addLast() | --|--|--|
Insert at Index | alist.**add**(i,v)| ll.add(i,v) | --|--|--|
**Edit**|
Replace at Index | alist.**set**(i,newVal)|ll.set(i,newVal)|map.**replace**(k,newVal);  map.replace(k,oldVal,newVal);|tmap.replace(k,newVal);  tmap.replace(k,oldVal,newVal);|--|
**Search**|
Contains k or v |alist.**contains**(v)|ll.contains(v)| map.**containsKey**(k)  map.**containsValue**(v)|tmap.containsKey(k)  tmap.containsValue(v)|tset.contains(v)|
Search First/Last Occurrence | alist.**indexOf**(v)   alist.**lastIndexOf**(v) | ll.indexOf(element)  ll.lastIndexOf(element)|--|--|--|
**Deletion**|
Remove First/Last| --|ll.**removeFirst**() or ll.**poll**()  ll.**removeLast**()|--|tmap.**pollFirstEntry**()  tmap.pollLastEntry()|tset.**pollFirst**()  tset.pollLast()|
Remove at index | alist.remove(i)|ll.remove(i)|map.remove(k)|tmap.remove(k)|--|
Remove element | alist.remove(v)|ll.**remove**((Object)obj)|--|--|tset.remove(v)|
**Retrieval**|
Fetch using k or i | alist.**get**(i)|ll.get(i)|map.get(k)|tmap.get(k)|--|
Fetch First/Last| -- | ll.**getFirst**() or ll.**peek**()  ll.**getLast**() | --| tmap.**firstKey**()  tmap.lastKey()|tset.**first**()  tset.last()|
**Extras**
Higher/Lower Key | --|--|--|tmap.**higherKey**(k)  tmap.**lowerKey**(k)|tset.**higher**(v)  tset.**lower**(v)|

### How to Sort
```
int arr[] = new int[n];
Arrays.sort(arr);
```

### ArrayList
alist.add()  
alist.add(index,element) 
alist.set(index,element) //replaces existing element  
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
LinkedList<String> ll = new LinkedList<String>()  
ll.addFirst(element) 
ll.addLast(element) or ll.add()    
  
ll.set(index, element)  // Resets earlier value at given index, invalid for index = ls.size()
ll.add(index,element)   // Add works as insertion of new node, is valid for index = ls.size()
  
ll.peek() //retrieves head without removal    
ll.get(index)  
ll.indexOf(element)  
ll.lastIndexOf(element)  
ll.contains(element)  

ll.poll() or ll.remove() or ll.removeFirst(); //retrieves and removes head  
ll.removeLast()  
ll.remove(index)  
arr.removeFirstOccurrence(element);
arr.removeLastOccurrence(element);

##### Implementation details:
* Non contiguous

### Hashmap
mp.containsKey(key)  
mp.containsValue(val)  
mp.replace(key,newValue); //blind replacement  
mp.replace(key,oldValue,newValue); //replaces only if oldValue matches  
mp.remove(key)

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
