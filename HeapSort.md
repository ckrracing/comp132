# comp132

#####Heap Sort

#####Building the Heap 

**Heap Sort** 
Definition: is a complete binary tree , that stores it's elements (nodes) with a heap property.

**Heap Property** 
  The order in which nodes are kept in the binary heap tree, where the Parent Node (P)  
  is greater than either of it's child nodes. 
  
  #####Building a Heap Algorithm
  
  ForEach Value **(v):
    ADD (v) to END of HEAP 
    REPEAT:
           COMPARE (V) to it's Parent (P)
           IF (P) > (V) you're done // change (P) < (V) FOR MIN HEAP SORT
           ELSE SWAP( (P) , (V) ) 
    END.

#####Number of Nodes in Tree
 **Log(base2)(N +1)**

#####Tree Height
 **O(LogN)**
 
 #####Runtime
 * To add each node: **O(Log N)**
 * To add N nodes: **(N Log N)**
 
 roughly half of the nodes in the heap are leaf nodes in the bottom of the tree. 
 
 
 #####Sorting the Heap.
 * Complete binary tree
 * Each node >= children
 
 #####HeapSort Algorithm 
 
 ADD all items to the heap (heapify)
    REPEAT until the heap is empty:
      REMOVE the root from the heap
      PUSH the last value in the heap to root
      PUSH the value down to fix the heap
      
**Note** that is different to when we add item to the heap where we PUSHUP() the node.

#####TOTAL Heap Sort Time

* Build the Heap: **O(N Log N)**
* Remove Items: **O(N Log N)**

* Total Time: **O(N Log N) + O(N Log N) = O(N Log N)**

#####Complete Binary Tree

* Each node has at most 2 children
* Leaf nodes are on the bottom and pushed to the left

How to find children of Parent Node (P) of **ZERO** based array  

ChildLH = (P) * 2 + 1 
ChildRH = (P) * 2 + 2 

** One ** based array 
ChildLH  = (P) * 2 ;
ChildRH  = (P) * 2 + 1;

IF ChildRH index > end of the array then it doesn't exist 

Find Parent of ChildX

floor( (indexOfChildX - 1) / 2 )

