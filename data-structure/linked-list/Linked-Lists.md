# Linked List 
# What is a linked list?

Linked list is a data structure implemented using a **linked structure** to store data values in a collection of nodes. In its most *basic form*, each node contains an element and a reference to the next node in the sequence of the list. Then each node of the list is linked to its next neighbor node, from the head to the tail and any number of nodes in between, except the last (tail) node points to null so it can end the list. 

## Step 1: Node Implementation

Linked list node is an object which contains an **element** and a **next** reference node, so it can be created from a class defined as follows in Java:

```
  class Node {
    int element;
    Node next;
    
    public Node(int element) {
      this.element = element;
    }
  }
```
  
Now that a node is created, we can inserted into the list and chain any additional nodes together to form a linked list. Since a new element can be added to the list, we can also remove it from the list. 

## Step 2: Declare head and tail

A linked list consists of any number of nodes chained together.
![singly linked list diagram](/linked-list/assets/images/figure26.7_linked_list.PNG)

## Step 3:

## Step 4:

## Insert
addFirst(data)
addLast(data)
add(index, data)
## Remove
removeFirst()
removeLast()
remove(index)
