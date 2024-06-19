Functionality | List
--|--
**Insertion**|
Insert| --| 
Insert at Start |
Insert at End | ls.append(val)
Insert at Index | ls.insert(i, val)
**Edit**|
Replace at Index | ls[i] = val
**Search**|
Contains k or v | val in ls
Search First/Last Occurrence | list.index(val[, start[, end]])
**Deletion**|
Remove First/Last| ls.pop() Removes last
Remove at index | ls.pop(i) or del ls[i]
Remove element | ls.remove(val) (removes first occurrance)
**Retrieval**|
Fetch using k or i | ls[i]
Fetch First/Last| ls[0], ls[-1] | 
**Extras**
Higher/Lower Key | --|--|--|tmap.**higherKey**(k)  tmap.**lowerKey**(k)|tset.**higher**(v)  tset.**lower**(v)|

## List
ls1.extend(iterable) 
newlist = [expression for item in iterable if condition == True] 
ls.sort() 
ls.sort(reverse=True) 
ls.count(val)
Lists can be used as stacks.

## General Notes
List: ordered, changeable, and allow duplicate values.
Set : unordered, no duplicates
Dict: no duplicates
