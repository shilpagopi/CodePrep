# Binary Tree - 1

### Basic Traversals
* Inorder: Left, Root, Right
* Preorder: Root, Left, Right
* Postorder: Left, Right, Root
* Levelorder:
 ```
 Add root to queue
 Add sentinel null node to Q
 
 while(Q.size()>1):
   pop n from Q
   
   if n==null
     add sentinel null to Q
     continue
     
   print(n)
   if n.left!=null, add to Q
   if n.right!=null, add to Q
   
 ```
 
 ### Special Traversals of Binary Tree
 
 * Level order traversal in spiral form
 
 > Print levels from r->l and l->r alternatively
 
 ```
 # Modify in above code:
 if level is odd:
    add right, add left
 else:
    add left, add right
 ```
 
  * Reverse Level order traversal 
    - Print from last level to first
    - Add right node, then left node to Q
    - Use stack to reverse order
 
 * Diagonal Traversal
 ```java
diagHashmap.get(d).add(root.val);  

// Traverse left child first - important
diagonalPrint(root.left, d + 1); 
diagonalPrint(root.right, d); 
 ```
Time: O(N), Space: O(N)
```python
def diagonalTraversal_iterative(root):
    if not root:
        return []

    result = []
    queue = deque()
    queue.append(root)

    while queue:
        current_node = queue.popleft()

        # Traverse along the current diagonal (moving right)
        while current_node:
            result.append(current_node.val)
            # If there's a left child, it starts a new diagonal, so enqueue it
            if current_node.left:
                queue.append(current_node.left)
            current_node = current_node.right # Move to the right child for the same diagonal
    return result
```
Time: O(N), Space: O(W) - where W is the widest diagonal to be stored in dq
### Diameter of Binary Tree
*Question-Pattern*: Return user-defined class, Post-compute
```java
Result diameterOpt(Node root) 
{ 
if (root == null) 
return new Result(0,0);
	  
Result left = diameterOpt(root.left); 
Result right = diameterOpt(root.right); 

Result r = new Result(0,0);
r.h = Math.max(left.h, right.h) + 1; 
r.d = Math.max(left.h + right.h + 1, Math.max(left.d, right.d));
return r; 
} 
```

### Get Next Leaf Function for a Binary Tree
*Question-Pattern*: DFS
```python
def get_next_leaf(self,ls):
while len(ls)>0:
    node = ls.pop()
    if node==None:
	return None
    if not node.left and not node.right:
	return node.val
    if node.right:
	ls.append(node.right)
    if node.left:
	ls.append(node.left)
return None
 ```
