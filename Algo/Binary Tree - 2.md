# Binary Tree - 2

### Node Finder
#### Lowest Common Ancestor (LCA)
*Question-Pattern*: Tricky
```java
public TreeNode lowestCommonAncestor(TreeNode root, TreeNode p, TreeNode q) {
    if (root==null)
        return null;
    if (root.val==p.val || root.val==q.val)
        return root;
    TreeNode left = lowestCommonAncestor(root.left,p,q);            
    TreeNode right = lowestCommonAncestor(root.right,p,q);

    if(left!=null && right!=null)
        return root;
    return left!=null?left:right;        
}
```

### Summation
#### Sum of all parent nodes having child node x
*Question-Pattern*: Pre-compute local variable, Return value + value of recursive calls
```java
int getSum(Node root,int x){
    if (root==null)
      return 0;
    int sum = 0;
    if((root.left!=null && root.left.val!=x)
       || (root.right!=null && root.right.val!=x))
      sum+=root.val;
    return sum+getSum(root.left,x)+getSum(root.right,x);
}
```
#### Sum of left leaves
*Question-Pattern*: Pass left/right child indicator as argument 
```java
int getSum(Node root,boolean isLeft){
    if(root==null)
      return 0;		
    if(isLeft && isLeaf(root))
      return root.val;
    return getSum(root.left,1)+getSum(root.right,0);	
}
```

#### Sum of heights of individual Nodes
*Question-Pattern*: Post-compute using global variable 
```java
int sum = 0;
int getHeight(Node root) 
{ 
    if (root == NULL) 
        return 0;   
    int lh = getHeight(root->left, sum); 
    int rh = getHeight(root->right, sum); 
    int h = max(lh, rh) + 1; 
    sum = sum + h; 
    return h; 
} 
```

#### Find largest subtree-sum (including root)
*Question-Pattern*: Post-compute using global variable 
```java
int maxsum = Integer.MIN_VALUE;
int getSum(Node root){
    if(root==null)
      return 0;
    int sum = root.val+getSum(root.left)+getSum(root.right);
    maxsum = maxsum<sum?sum:maxsum;
    return sum;	
} 
