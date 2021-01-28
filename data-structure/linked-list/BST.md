### Search
```java
  public boolean search(int e) {
    TreeNode current = root;
    
    while(current != null) {
      if(e < current.ele) {
        current = current.left;
      } else if(e > current.ele) {
        current = current.right;
      } else {
        return true;
      }
    }
    
    return false;
  }
```


### Insert
```java
  public boolean insert(int e) {
    if(root == null) {
      root = new TreeNode(e);
    } else {
      TreeNode parent = null;
      TreeNode current = root;
      
      while(current != null) {
        if(e < current.ele) {
          parent = current;
          current = current.left;
        } else if(e > current.ele) {
          parent = current;
          current = current.right;
        } else {
          return false;
        }
      }
      
      // insert
      if(e < cuurent.ele) {
        parent.left = new TreeNode(e);
      } else {
        parent.right = new TreeNode(e);
      }
    }
    size++;
    return true;
  }
```
