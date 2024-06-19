Functionality | List | Set
--|--|--
**Insertion**||
Insert| --| |
Insert at Start ||
Insert at End | ls.append(val)|
Insert at Index | ls.insert(i, val)|
**Edit**||
Replace at Index | ls[i] = val|
**Search**||
Contains k or v | val in ls|
Search First/Last Occurrence | list.index(val[, start[, end]])|
**Deletion**||
Remove First/Last| ls.pop() Removes last|
Remove at index | ls.pop(i) or del ls[i]|
Remove element | ls.remove(val) (removes first occurrance)|
**Retrieval**||
Fetch using k or i | ls[i]|
Fetch First/Last| ls[0], ls[-1] | 
**Constructors**||
Definition | ls = [1,2,"hi"] or ls = list(iterable)| s= set() or s = {1,2,3}
**Extras**
list comprehensions | squares = [x**2 for x in ls]|

## List
ls1.extend(iterable) \
newlist = [expression for item in iterable if condition == True] \
ls.sort() \
ls.sort(reverse=True) \
ls.count(val)

## Set
set_union = set1.union(set2) \
set_union = set1 | set2 \
set_intersection = set1.intersection(set2)v
set_intersection = set1 & set2 \
set_difference = set1.difference(set2) \
set_difference = set1 - set2

## General Notes
List: ordered, changeable, and allow duplicate values, can be used as stacks \
Set : unordered, no duplicates, faster than lists to check for unique values \
Dict: no duplicates, Ordered in Python 3.6.0 and later versions \
Deque vs List: Access element - list O(1), deque O(n). Insert element at start: list O(n), deque O(1) \
Tuples: immutable, can be used as dictionary keys if all their elements are immutable, cannot be copied, occupy more memory than lists.
