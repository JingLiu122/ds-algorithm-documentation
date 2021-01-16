# Linked List 
# Table of Content:
[Inserting Nodes](#insertion)


# What is a linked list?

Linked list is a data structure implemented using a **linked structure** to store data values in a collection of nodes. Usually, each node contains an element and a reference to the next node in an sequential order of the list. Then each node of the list is linked to its next neighbor node, from the head to the tail and any number of nodes in between, except the last (tail) node is pointed to null so it can end the list, as shown in Figure 1. 

How to traverse a linked list?

## Step 1: Node Implementation

Linked list node is an object which contains an **element** and a **next** reference node, so it can be created from a class defined as follows in Java:

```java
  class Node {
    String element;
    Node next;
    
    public Node(String element) {
      this.element = element;
    }
  }
```
  
Now that a node is created, we can inserted into the list and chain any additional nodes together to form a linked list. Since a new element can be added to the list, we can also remove it from the list. 


### Figure 1:
| ![singly linked list diagram](/data-structure/assets/images/figure26.7_linked_list.PNG) |
|:--:|
| *A linked list consists of any number of (n) nodes chained together.* |
<br>


## Step 2: Declare head and tail

First, we need to delcare a head and tail variable to reference the list, so we know where it is store in a memory location; access nodes of the list and modify them.

For example, here's a code snippet to initialize the head and tail to null because the list is empty initially:
```java
  Node head = null;
  Node tail = null;
```

# Insertion
## Step 3: Inserting Nodes

There are three methods that can be inserted a new node into a linked list, as describe in below examples:

### Code snippet to implement insertion methods:
#### 1. addFirst(data)
```java
  public void addFirst(String element) {
    Node newNode = new Node(element);
    newNode.next = head;
    head = newNode;
    if(tail == null) tail = head;
    size++;
  }
```
First, this method creates a new node to store the element and inserts the node at the beginning of the list. Then set the `next` variable of the new node references to the head of the list. After the insertion, set `head` points to this new element node. Now this new node is chained together with the list. Last but not least, if the `tail` is null, that means the list is empty (initial list), then just set both `tail` and `head` point to this first newly inserted node of the list, as shown in Figure 2.1a to Figure 2.1c). Finally increase the size of the linked list by 1. 

#### Figure 2.1: Better visual explanation to add a new element at the beginning of the list.
##### Figure 2.1a
| ![addFirst before insertion](/data-structure/assets/images/Figure2.1a.PNG) |
|:--:|
| *Before a new node is inserted at the beginning of the list.* |
<br>

##### Figure 2.1b
| ![addFirst while insertion](/data-structure/assets/images/Figure2.1b.PNG) |
|:--:|
| *Link the new node with the head.* |
<br>

##### Figure 2.1c
| ![addFirst after insertion](/data-structure/assets/images/Figure2.1c.PNG) |
|:--:|
| *After a new node is inserted.* |
<br>


#### 2. addLast(data)
```java
  public void addLast(String element) {
    Node newNode = new Node(element);
    if(tail == null) {
      head = tail = newNode;
    } else {
      tail.next = newNode;
      tail = newNode;
    }
    size++;
  }
```
This method creates a new node to hold the element and appends at the end of the list. While inserting, there are two cases that need to be considered in here: 
1) If it is an empty list, set both set and tail points to this new node, as shown in Fiure 2.2.1a and Figure 2.2.1b.
2) Otherwise, link this new node with the last (tail) node in the list. Then set `tail` points to this new node, so this node becomes the last node of the list (shown in Figure 2.2.2a to Figure 2.2.2d).
Finally, in any the cases, after the node is created, increase the size by 1.

#### Figure 2.2: Better visual explanation to add a new element at the end of the list.

#### Case 1:
##### Figure 2.2.1a
| ![addLast case 1 before insertion](/data-structure/assets/images/Figure2.2.1a.PNG) |
|:--:|
| *Before a new node is inserted in an empty list.* |
<br>

##### Figure 2.2.1b
| ![addLast case 1 after insertion](/data-structure/assets/images/Figure2.2.1b.PNG) |
|:--:|
| *After a new node is inserted in an empty list.* |
<br>

#### Case 2:
##### Figure 2.2.2a
| ![addLast case 2 before insertion](/data-structure/assets/images/Figure2.2.2a.PNG) |
|:--:|
| *Before a new node is inserted at the end of the list.* |
<br>

##### Figure 2.2.2b
| ![addLast case 2 during insertion](/data-structure/assets/images/Figure2.2.2b.PNG) |
|:--:|
| *Link the new node with the last node in the list.* |
<br>

##### Figure 2.2.2c
| ![addLast case 2 during insertion](/data-structure/assets/images/Figure2.2.2c.PNG) |
|:--:|
| *Set tail points to the last node.* |
<br>

##### Figure 2.2.2d
| ![addLast case 2 after insertion](/data-structure/assets/images/Figure2.2.2d.PNG) |
|:--:|
| *After a new node is inserted.* |
<br>


#### 3. add(index, data)
```java
  public void add(int index, String element) {
    if (index == 0) addFirst(element);
    else if(index >= size) addLast(element);
    else {
      Node prevNode = head;
      
      for(int i = 1; i < index; i++) {
        prevNode = prevNode.next;
      }
      
      Node temp = prevNode.next; // current node 
      prevNode.next = new Node(element);
      (prevNode.next).next = temp;
      size++;
    }
  }
```
This method inserts an element into the list at the specified index. However there are three cases that need to be considered when inserting: 
1) If `index` is 0, then the element is going to be inserted at the beginning of the list, invoke `addFirst(data)` to do the work. 
2) If `index` is greater than or equal to the size of the list, then insert the element at the end of the list, invoke `addLast(data)` this time.
3) Otherwise, create a new node to hold the new element and insert it in the middle of the list (at a specific index -- zero-based indexing like in the array). As shown in Figure 2.3a, locate the current node of a specific index position that is going to insert a new element node, and store it to the `temp` node for reference. Then insert it into the list by linking the previous node (`prevNode`) of the located current node to this new node (`newNode`), and then `newNode` links to `temp` to chain them together as a new linked list, as shown in Figure 2.3b. The final result is shown in Figure 2.3c. Finally, increase the size of the list by 1.

#### Figure 2.3: Better visual explanation to add a new element in the middle of the list.
##### Figure 2.3a
| ![add method before insertion](/data-structure/assets/images/Figure2.3a.PNG) |
|:--:|
| *Before a new node is inserted at a specified index position.* |
<br>

##### Figure 2.3b
| ![add method during insertion](/data-structure/assets/images/Figure2.3b.PNG) |
|:--:|
| *While inserting, prevNode.next links to newNode, and newNode.next links to temp.* |
<br>

##### Figure 2.3c
| ![add method after insertion](/data-structure/assets/images/Figure2.3c.PNG) |
|:--:|
| *After a new node is inserted at a specified index position.* |
<br>


## Step 4: Deleting Nodes

Removing nodes from a linked list can be done by a similar approach as inserting. 

### Code snippet to implement deletion methods:
#### 1. removeFirst()
```java
  public String removeFirst() {
    if(size == 0) {
      return "-1";
    } else {
      Node temp = head;
      head = head.next;
      if(head == null) tail = null;
      size--;
      return temp.element;
    }
  }
```
This method removes the element of the first node from the list. But first, there are two cases need to be considered:
1) If the list is empty, there is nothing to delete, so return `-1` for indication.
2) Otherwise, remove the first node from the list by simply pointing `head` to the second node (`head.next`). But first we need to create a `temp` node to keep the first node of the list temporarily, as shown in Figure 3.1b. If when the list becomes empty after a node we just removed, that means there was only one node in the list, then set the tail to `null`. Reduce the size by 1 and finally return the deleted element. 

#### Figure 3.1: Better visual explanation to remove the first node from the list.
##### Figure 3.1a
| ![remove first method before deletion](/data-structure/assets/images/Figure3.1a.PNG) |
|:--:|
| *Before the node is deleted from the beginning of the list.* |
<br>

##### Figure 3.1b
| ![remove first method after deletion](/data-structure/assets/images/Figure3.1b.PNG) |
|:--:|
| *After the node is deleted from the beginning of the list.* |
<br>


#### 2. removeLast()
```java
  public String removeLast() {
    if(size == 0) {
      return "-1";
    } else if(size == 1) {
      Node temp = tail;
      head = tail = null;
      size = 0;
      return temp.element;
    } else {
      Node prevNode = head;
      
      for(int i = 0; i < size-2; i++) {
        prevNode = prevNode.next;
      }
      
      Node temp = tail;
      tail = prevNode;    // previous node of the last node (the second-to-last node)
      tail.next = null;
      size--;
      return temp.element;
    }
  }
```
This method removes the element of the last node from the list. Consider three cases:
1) If the list is empty, return `-1`.
2) If the list contains only one node, return the element of this node and then destory it by set both `head` and `tail` point to null; Java garbage collection handles the work over here. Then the size of the list becomes 0 after the deletion. 
3) Otherwise, traverse the list to locate the second-to-last node and reposition `tail` to point to this node, and then set the next of the tail node to null to end the list, as shown in Figure 3.2b. Finally, reduce the size by 1 and return the element of the deleted node. 

#### Figure 3.2: Better visual explanation to remove the last node from the list.
##### Figure 3.2a
| ![remove last method before deletion](/data-structure/assets/images/Figure3.2a.PNG) |
|:--:|
| *Before the node is deleted from the end of the list.* |
<br>

##### Figure 3.2b
| ![remove last method during deletion](/data-structure/assets/images/Figure3.2b.PNG) |
|:--:|
| *Deleting the last node from the list.* |
<br>

##### Figure 3.2c
| ![remove last method after deletion](/data-structure/assets/images/Figure3.2c.PNG) |
|:--:|
| *After the node is deleted from the end of the list.* |
<br>


#### 3. remove(index)
```java
  public String remove(index) {
    if(index < 0 || index >= size) return '-1';
    else if(index == 0) return removeFirst();
    else if(index == size - 1) return removeLast();
    else {
      Node prevNode = head;
      
      for(int i = 1; i < index; i++) {
        prevNode = prevNode.next;
      }
      
      Node temp = prevNode.next;   // current node
      prevNode.next = temp.next;
      size--;
      return temp.element;
    }
  }
```
This method finds the node at the specified index and then removes it. Consider four cases:
1) Check the edge cases: if `index` is negative or beyond the range of the list (`index` is zero-based, and `size` is the length of the list like an array), return `-1`.
2) If `index` is 0, invoke `removeFirst()` to remove the first node from the list.
3) If `index` is the end position of the list, which is `size - 1`, then invoke `removeLast` to remove the last node from the list. 
4) Otherwise, traverse the list and locate the node at the specified `index`. Then let `temp` denote this current node that is going to delete, which is `prevNode.next` in the list., as shown in Figure 3.3b. Next, link the previous node `next` to the current node's next nrighbor, which is to assign `temp.next` to `prevNode.next` to destroy the current node, as shown in Figure 3.3b. Finally, reduce the size by 1 and return the element of the deleted node.  

#### Figure 3.3: Better visual explanation to remove the node at a specified index
##### Figure 3.3a
| ![remove method before deletion](/data-structure/assets/images/Figure3.3a.PNG) |
|:--:|
| *Before the node is deleted.* |
<br>

##### Figure 3.3b
| ![remove method during deletion](/data-structure/assets/images/Figure3.3b.PNG) |
|:--:|
| *Deleting the node from the list.* |
<br>

##### Figure 3.3c
| ![remove method after deletion](/data-structure/assets/images/Figure3.3c.PNG) |
|:--:|
| *After the node is deleted.* |
<br>

# Variations of Linked Lists
The linked list introcuded in the preceding examples is known as singly linked list. There's also doubly linked list, circular linked list, and circular doubly linked list.













