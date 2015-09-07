# comp132

####Heap Sort

**Heap Sort** 
Definition: is a complete binary tree , that stores it's elements (nodes) with a heap property.

**Heap Property** 
  The order in which nodes are kept in the binary heap tree, where the Parent Node (P)  
  is greater than either of it's child nodes. 
  
  ####Building a Heap Algorithm
  
  ForEach Value **(v):
    ADD (v) to END of HEAP 
    REPEAT:
           COMPARE (V) to it's Parent (P)
           IF (P) > (V) you're done // change (P) < (V) FOR MIN HEAP SORT
           ELSE SWAP( (P) , (V) ) 
    END.

####Number of Nodes in Tree
 **Log(base2)(N +1)**

####Tree Height
 **O(LogN)
 
