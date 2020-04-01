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
 
 ### Special Traversals
 
 * Level order traversal in spiral form
 
 > Print levels from r->l and l-> alternatively
 
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
 ```
diagHashmap.get(d).add(root.val);  

// Traverse left child first - important
diagonalPrint(root.left, d + 1); 
diagonalPrint(root.right, d); 
 ```

 
