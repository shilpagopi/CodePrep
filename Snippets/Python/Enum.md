# Enum - Enumerations

* Enum is a set of symbolic names (members) bound to unique values
* Enums can be iterated over to return its canonical members in definition order (for x in Season: print(x.value))
* Hashable, Comparable (Identity (is, is not) and Equality (==, !=))


### 

```python
from enum import Enum
 
class Seasons(Enum):
    SPRING = 1
    SUMMER = 2
    AUTUMN = 3
    WINTER = 4
```
### names() and values() - returns enum names and values resp.
```python
print(Seasons.SPRING.name) => SPRING
print(Seasons.SPRING.value) => 1
```
### Mapping from string or int
```python
Seasons['SPRING'] => Seasons.SPRING
Seasons(3)=>Seasons.AUTUMN
```

### Supports multiple value mapping
```python
class Seasons(Enum):
    SPRING = 1, 'Sp'
print(Seasons.SPRING.value[1])
```

### Constructors
How to create a variable based on enum value
```python
class Squares(Enum):
    BLUE = 3
    RED = 2
    
    def __init__(self, value):
    	self.area = value*value
     
print(Squares.BLUE.area)
```

Constructor variable list gets extended by default:
```python
from enum import Enum

class Squares(Enum):
    BLUE = 3, 'b'
    RED = 2, 'r'
    
    def __init__(self, side, single_char):
        self.area = side*side
        self.c = single_char
     
print(Squares.BLUE.c)
print(Squares.BLUE.area)
```
