Functionality | List |Deque | Set | Dict | SortedSet|SortedList|SortedDict
--|--|--|--|--|--|--|--
**Insertion**|||||||
Insert| --|--| s.add(val)| dict[k]=v|sortedset.add(v)|sortedlist.add(v)|sorteddict[k]=v
Insert at Start||q.appendleft(val)|--|--|--|--|--
Insert at End |ls.append(val)|q.append(val)|--|--|--|--|--
Insert at Index | ls.insert(i, val)|q.insert(i, val)|--|--|--|--|--
**Edit**|||||||
Replace at Index | ls[i] = val|q[i]=val #inefficient||dct[k]=new_val|--|--|sorteddict[k]=new_val
**Search**|||||||
Contains k or v | val in ls|val in q| val in s| k in dct | in | in | in
Search First/Last Occurrence | list.index(val[, start[, end]])|q.index(val[, start[, end]])| |--|sortedset.index(key)|sortedlist.index(key)|sorteddict.index(key)
Count|ls.count(val)|q.count(val)|--|--|--|sortedlist.count(key)|sorteddict.count(key)
**Deletion**|||||||
Remove First|--|q.popleft()|--| In ordered dict, od.popitem(last = False)|sortedset.pop(0)|sortedlist.pop(0)|sorteddict.popitem(0)
Remove Last |ls.pop() Removes last|q.pop()||In ordered dict, od.popitem()|sortedset.pop()|sortedlist.pop()|sorteddict.popitem()
Remove at index | ls.pop(i) or del ls[i]|--|--|del dict[key]|sortedset.pop(index)|sortedlist.pop(index)|sorteddict.popitem(index)
Remove element(#raises error if val not present) | ls.remove(val) (removes first occurrance)|q.remove(val) (removes first occurrance)|s.remove(val),  s.discard(val) - no error if absent| --|sortedset.remove(v) <br> sortedset.discard(v)|sortedlist.remove(v) <br> sortedlist.discard(v)|
**Retrieval**|||||||
Fetch using k or i | ls[i]|q[i] #ineffifcient||dct[k]|--|sortedset[i]|sortedlist[i]|sorteddict.peekitem[i]
Fetch First/Last| ls[0], ls[-1] |q[0], q[-1]|||--|--|--
**Constructors**||||||
Definition | ls = [1,2,"hi"] or ls = list(iterable); arr = [[0] * 4 for i in range(4)]|q = deque() or q = deque(iterable)| s= set() or s= set(iterable) or s = {1,2,3}| d = {} or d = OrderedDict()|from sortedcontainers import SortedSet <br> slist = SortedSet([1, 2])|from sortedcontainers import SortedList <br> slist = SortedList([1, 2])|from sortedcontainers import SortedDict <br> d = SortedDict({3: 'c', 1: 'a', 2: 'b'})
**Extras**||||
Extra functions:|list comprehensions squares = [x**2 for x in ls]; nums.reverse()  |q.rotate(-3) #rotate 3 to left|s.update(iterable)|popitem(),move_to_end()||bisect_left(key) or bisect_right(key):Finds an insertion point for a new key, to the left/right of existing entries if the key is present.|Valid for both SortedDict and SortedList

## List
ls1.extend(iterable) \
newlist = [expression for item in iterable if condition == True] \
ls.sort() \
ls.sort(reverse=True) \
ls.count(val)  
ls.reverse()

## Set
set_union = set1.union(set2) \
set_union = set1 | set2 \
set_intersection = set1.intersection(set2)v
set_intersection = set1 & set2 \
set_difference = set1.difference(set2) \
set_difference = set1 - set2

## Dict
Dict comprehension
myMap = { i: 2*i for i in range(3) }

Looping through maps  
for key in myMap:
    print(key, myMap[key])

for val in myMap.values():
    print(val)

for key, val in myMap.items():
    print(key, val)

from collections import defaultdict  
d = defaultdict(list) # []  
d = defaultdict(str) # ""  
d = defaultdict(int) # 0  
d = defaultdict(lambda: "Not Present")  

## Ordered Dict
#### * popitem() * move_to_end()
```python
from collections import OrderedDict
od = OrderedDict()
od['a'] = 1
od['b'] = 2
od['c'] = 3
od['d'] = 4
od['e'] = 5
od['f'] = 6

#od.pop('f')
del od['f']
    
print(od.popitem()) ->('e', 5)
print(od.popitem(last = False)) ->('a', 1)
od.move_to_end('c')
print(od) ->OrderedDict([('b', 2), ('d', 4), ('c', 3)])
od.move_to_end('c', last= False)
print(od) ->OrderedDict([('c', 3), ('b', 2), ('d', 4)])
```

## Heapq (always a min heap)
```python
from heapq import heapify, heappop, heappush
li = [5, 7, 9, 1, 3]
heapify(li)
heappush(li,4)
print(heappop(li)) #smallest element
# Min is always at index 0
print(li[0])
```

## General Notes
List: ordered, changeable, and allow duplicate values, can be used as stacks \
Deque: ordered, allows duplicates, efficient first element access, inefficient random elem access
Deque vs List: Access element - list O(1), deque O(n). Insert element at start: list O(n), deque O(1) \
Set : unordered, no duplicates, faster than lists to check for unique values, Only immutable types can be added to a Python set. \
Dict: no duplicates, Ordered in Python 3.6.0 and later versions \

Tuples: immutable, can be used as dictionary keys if all their elements are immutable, cannot be copied, occupy more memory than lists.

Copying: 
import copy \
li2 = copy.copy(any) # Only creates copies immutable objects. Mutable object references remain same. \
li3 = copy.deepcopy(any) # Creates nested copies of all objects \

