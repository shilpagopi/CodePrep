# Binary Search Tree - 1
### Node Searching
```python
public search(root, key) 
{ 
    if (root==null || root.key==key) 
        return root; 
    if (root.key > key) 
        return search(root.left, key); 
    return search(root.right, key); 
} 
```
### Node Insertion
```python
def insert(root, key):
    # Base Case: If the tree is empty, return a new node
    if root is None:
        return Node(key)
    
    # Recursive Step: Traverse the tree to find the correct insertion spot
    if key < root.key:
        root.left = insert(root.left, key)
    elif key > root.key:
        root.right = insert(root.right, key)

    return root
 ```
  
### Node Deletion
Method: Search for the node and append the modified tree returned 
If Node to be deleted 
1) is leaf: Simply remove from the tree.
2) has only one child: Copy the child's value to the node and delete the child recursively
3) has two children: Find its inorder successor(s),i.e.,minimum node from right tree. Copy value of s to the node and delete s. 
(Note that inorder predecessor can also be used.)
```java
public TreeNode getMinimumNode(TreeNode root){
	while(root!=null && root.left!=null)
		root = root.left;
	return root;
}

public TreeNode deleteNode(TreeNode root, int key) {
	//For appending the modified tree back
	if(root==null)
		return root;
	if(root.val<key)
		root.right = deleteNode(root.right,key);
	else if(root.val>key)
		root.left = deleteNode(root.left,key);
	
	//identified the node to be deleted 
	else {
	        //leaf
		if(root.right==null && root.left==null)                
			return null;
			
		//single child
		if(root.right==null)
			return root.left;
		else if(root.left==null)
			return root.right;
			
		//has 2 children	
		else {
			TreeNode insucc = getMinimum(root.right);
			root.val = insucc.val;
			root.right = deleteNode(root.right,insucc.val);
		}
	}	
	return root;
}
```
Worst case: Time:O(N),Space:O(1); Most optimized(for balanced BST): Time:O(log N),Space:O(1)
