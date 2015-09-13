# comp132

#####Heap Sort

#####Building the Heap 

**Heap Sort** 
Definition: is a complete binary tree ,  with the heap property.

**Heap Property** 
  The order in which nodes are kept in the binary heap tree, where the Parent Node (P)  
  is greater OR less than either of it's child nodes depending on if it's a MIN HEAP or MAX HEAP tree.
  
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

#####Binary Tree Terminology

* root
* leaves nodes at the bottom of the tree
* direct ancestor is Parent
* direct descendants children
* have at most 2 children
* **level** length of the path from root to node N
* **depth** longest path from root to a leaf

A binary tree T with depth D is complete if.


1. T has 2^L nodes for each level L, where 0 <= L <=D -1 , that is each level other than the last  
must have no free nodes. 
2. All leaf nodes at level D are as far to the left as possible.  


Number of nodes in a perfectly balanced binary tree of depth D is 

# nodes = 2^0 + 2^1 + 2^2 .. + 2^d = 2^d+1 - 1. 

So 2^d -1 < # number of Nodes <= 2^(d+1) -1 

D ~ log(base2)(# of nodes). //depth of the tree is approx equal to 

So longest path from root to a leaf node is of the order **O(log N)** where N is the number  
of nodes in the complete binary tree. 

A node A[k] is a leaf if 2k + 1 >= n (end of the array)
A node A[k] has left child if 2k +1 < n 
A node A[k] has right child if 2k + 2 < n 

rightmost leaf is A[n-1] where n is size of the heap. 

