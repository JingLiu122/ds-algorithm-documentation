# Linked List 
# What is a linked list?

Linked list is a data structure implemented using a **linked structure** to store data values in a collection of nodes. In its most *basic form*, each node contains an element and a reference to the next node in the sequence of the list. Then each node of the list is linked to its next neighbor node, from the head to the tail and any number of nodes in between, except the last (tail) node points to null so it can end the list. 

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

There are three methods that can be inserted a new node into a linked list, and each method have three cases that need to be considered when inserting: when there is/are 0 nodes (the list is empty), 1 node, and n nodes in the list. And the same goes to the removing operation. 

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

### Figure 2


## Step 4: Deleting Nodes

## Remove
removeFirst()
removeLast()
remove(index)
