# Linked List 
# What is a linked list?

Linked list is a data structure implemented using a **linked structure** to store data values in a collection of nodes. In its most *basic form*, each node contains an element and a reference to the next node in the sequence of the list. Then each node of the list is linked to its next neighbor node, from the head to the tail and any number of nodes in between, except the last (tail) node points to null so it can end the list, as shown in Figure 1. 

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
First, this method creates a new node to store the element and inserts the node at the beginning of the list. Then set the `next` variable of the new node references to the head of the list. After the insertion, set `head` points to this new element node. Now this new node is chained together with the list. Last but not least, if the `tail` is null, that means the list is empty (initially), then just set both `tail` and `head` point to this first newly inserted node of the list. Finally increase the size of the linked list by 1. 

The algorithm is shown in the figures below to have a better visual explaination:

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
(1) If it is an empty list, set both set and tail points to this new node, as shown in Fiure 2.2.1a and Figure 2.2.1b.
(2) Otherwise, link this new node with the last (tail) node in the list. Then set `tail` points to this new node, so this node becomes the last node of the list (shown in Figure 2.2.2a to Figure 2.2.2d).
Finally, in any the cases, after the node is created, increase the size by 1.

#### igure 2.2: Better visual explanation to add a new element at the end of the list.

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
    if(index < 0) {
      System.out.println("Invalid index!");
      return;
    } 
    else if (index == 0) addFirst(element);
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
(1) If `index` is 0, then the element is going to be inserted at the beginning of the list, invoke `addFirst(data)` to do the work. 
(2) If `index` is greater than or equal to the size of the list, then insert the element at the end of the list, invoke `addLast(data)` this time.
(3) Otherwise, create a new node to hold the new element and insert it in the middle of the list (at a specific index -- zero-based indexing like in the array). As shown in Figure 2.3a, locate the current node of a specific index position that is going to insert a new element node, and store it to the `temp` node for reference. Then insert it into the list by linking the previous node (`prevNode`) of the located current node to this new node (`newNode`), and then `newNode` links to `temp` to chain them together as a new linked list, as shown in Figure 2.3b. Finally, increase the size of the list by 1.

#### Figure 2.3: Better visual explanation to add a new element in the middle of the list.
##### Figure 2.3a
| ![add method before insertion](/data-structure/assets/images/Figure2.3a.PNG) |
|:--:|
| *Before a new node is inserted* |
<br>





## Step 4: Deleting Nodes

## Remove
removeFirst()
removeLast()
remove(index)
