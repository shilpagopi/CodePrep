# Binary Tree - 3

#### Serialization
#### Check if a tree is a subtree of another:
*Question-Pattern*: **Update/Construct whole tree and return updated tree's root** 

* Binary Search Trees: only preorder or postorder traversal is sufficient to store structure information.
* Complete Binary Tree: level order traversal is sufficient to store the tree. 
* Full Tree: Store preorder traversal and store a bit with every node to indicate whether the node is an internal node or a leaf node.
* Generic Binary Tree:
  * Store both Inorder and Preorder traversals
  * Store Preorder traversal and a marker for NULL pointers
  * Store Preorder traversal, store a IsLeafBit with every node, a marker for null pointers
 N-ary tree: Store an ‘end of children’ ("\") marker with every node. 

```python
        if not root:
            return "(#)"
        return f"({root.val},{self.serialize(root.left)},{self.serialize(root.right)})"
        # Braces are important to prevent partial incorrect overlap.
 ```

 
```python
def serialize(root):
    if root is None:
        return ["#"]
    # Pre-order traversal
    return [str(root.data)] + serialize(root.left) + serialize(root.right)

index = 0	
def deserialize(data):
    # Base case: If the current element is the null marker, return None.
    if index >= len(data) or data[index] == "#":
        # Increment the index for the next recursive call
        index += 1
        return None

    val = data[index]
    node = Node(int(val))
    index += 1

    node.left = deserialize(data, index)
    node.right = deserialize(data, index)

    return node
```
