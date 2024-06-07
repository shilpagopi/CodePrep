# Comparable for Custom Classes
```python
class Fruit():
    def __init__(self, name, price):
        self.name = name
        self.price = price        
            
    def __lt__(self, other_item):
    	return len(self.name)<len(other_item.name)

    def __eq__(self, other_item): #not mandatory, but better to define all comparisons
    	return len(self.name)==len(other_item.name)

L = [Fruit("Cherry", 10), Fruit("Apple", 5), Fruit("Blueberry", 20)]
len_sorted = sorted(L)
price_sorted = sorted(L, key=lambda x: x.price, reverse = True)

print(f'Length: {[x.name for x in len_sorted]}')
print(f'Price: {[x.name for x in price_sorted]}')
```

# Equality
```python
class Fruit():
    def __init__(self, name, size):
        self.name = name 
        self.size = size
            
    def __lt__(self, other_item):
    	return len(self.name)<len(other_item.name)
    
    def __eq__(self, other_item):
    	return self.size == other_item.size

cherry = Fruit("Cherry", "small")
pineapple = Fruit("Pineapple", "big")
blueberry = Fruit("Blueberry", "small")

#checking equality in terms of size
print(cherry == blueberry) =>True
print(cherry == pineapple) =>False

#checking less than in terms of len(name)
print(cherry < pineapple) =>True
print(pineapple < blueberry)=>False
```
