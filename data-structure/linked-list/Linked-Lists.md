# Linked List 
# What is a linked list?

Linked list is a data structure implemented using a **linked structure** to store data values in a collection of nodes. In its most *basic form*, each node contains an element and a reference to the next node in the sequence of the list. Then each node of the list is linked to its next neighbor node, from the head to the tail and any number of nodes in between, except the last (tail) node points to null so it can end the list. 

## Step 1: Node Implementation

Linked list node is an object which contains an **element** and a **next** reference node, so it can be created from a class defined as follows in Java:

```java
  class Node {
    int element;
    Node next;
    
    public Node(int element) {
      this.element = element;
    }
  }
```
  
Now that a node is created, we can inserted into the list and chain any additional nodes together to form a linked list. Since a new element can be added to the list, we can also remove it from the list. 


### Figure 1 
An example in a figure to illustrate that a linked list holds n nodes in sequence: 
| ![singly linked list diagram](/data-structure/assets/images/figure26.7_linked_list.PNG) |
|:--:|
| *A linked list consists of any number of nodes chained together.* |


## Step 2: Declare head and tail

First, we need to delcare a head and tail variable to reference the list, so we know where it is store in a memory location; access nodes of the list and modify them.

For example, here's a code snippet to initialize the head and tail to null because the list is empty initially:
```java
  Node head = null;
  Node tail = null;
```

## Step 3: Inserting Nodes 

### Figure 2

## Step 4: Deleting Nodes

## Insert
addFirst(data)
addLast(data)
add(index, data)
## Remove
removeFirst()
removeLast()
remove(index)
