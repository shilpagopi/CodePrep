# Comparable for Custom Classes
```python
class Fruit():
    def __init__(self, name, price):
        self.name = name
        self.price = price        
            
    def __lt__(self, other_item):
    	return len(self.name)<len(other_item.name)

L = [Fruit("Cherry", 10), Fruit("Apple", 5), Fruit("Blueberry", 20)]

len_sorted = sorted(L)
price_sorted = sorted(L, key=lambda x: x.price, reverse = True)

print(f'Length: {[x.name for x in len_sorted]}')
print(f'Price: {[x.name for x in price_sorted]}')
```
