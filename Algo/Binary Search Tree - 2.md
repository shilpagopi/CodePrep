# Binary Search Tree - 2
### Node Finder
#### Get Inorder Successor
**Question-Pattern**: Passing a "val until now" or constraint in the argument.
Irrespective of key being present or absent, get next larger value, if exists.
```java
public TreeNode getMinimum(TreeNode root){
    while(root!=null && root.left!=null)
      root = root.left;
    return root;
}

TreeNode findInorderSuccessor(TreeNode root, TreeNode succ, int key)
{
    if (root==null) #key absent
        return succ;
    if (key > root->data) //successor lies in right tree
          return findInorderSuccessor(root->right,key);    
    else if (key < root->data)
    {
        succ = root; //root node is a potential successor
        return findInorderSuccessor(root->left,succ,key);
    }
    else // node value = key #key present
    {
        if (root->right)
            return getMinimum(root->right);
    }
    return succ;
}
```
#### LCA of two TreeNodes(n1,n2) in Binary Search Tree
> The first node n such that n1<=n<=n2  
> if n>n1 and n>n2, go left, else go right

#### Kth largest element in BST:
**Question-Pattern**: Passing a "val until now" or constraint in the argument.
```java
// Reverse inorder traversal with count
int k=0
def inorder(root):
  if(root==null || k>=K)
    return;
  inorder(root.right)
  k+=1
  if(k==K) print(root.val)
  inorder(root.left)
```

#### Find largest node <=K
**Question-Pattern**: In BST, iterative approach with global variable can be used if only one path (left or right) needs to be checked
```java
def findNum (node,K)
{
    Integer ans = Null;
    while (node)
    {
        if (node.val==K)
            return K;

        if (node.val>K)
            node = node.left;
        else
        {
            ans = node.val;
            node = node.right;
        }
    }
    return ans;
}
```

#### Is Valid BST ?
**Question-Pattern**: Passing constraint(s) in the argument.
```java
isBST(node, INT_MIN, INT_MAX)

def isBST(node, mini, maxi): 
    if node is None: 
        return True
    if node.data <= mini or node.data >= maxi: 
        return False
    return (isBST(node.left, mini, node.data -1) and
          isBST(node.right, node.data+1, maxi)) 
```

