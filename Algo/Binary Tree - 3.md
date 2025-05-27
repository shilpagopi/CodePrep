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
  
```java
public void serialize(Node root, ArrayList<Integer> A) {
	    if(root==null){
	        A.add(-1);
	        return;
	    }
	    
	    A.add(root.data);
	    serialize(root.left, A);
	    serialize(root.right, A);
	}
	
  public Node deSerialize(ArrayList<Integer> A){
      if(A.size()==0)
          return null;
      if(A.get(0)==-1){
          A.remove(0);
          return null;
      }    
      Node n = new Node(A.get(0));
      A.remove(0);
      n.left = deSerialize(A);
      n.right = deSerialize(A);
      return n;
    }
```
