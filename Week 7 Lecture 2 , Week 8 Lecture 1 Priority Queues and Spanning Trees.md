#### Recap from last week

##### Heaps
> A **complete** binary tree with the heap order property .  
**Heap Order Property** is when the heap is in an order (partial) where **every** parent is less than it's children.  

Heaps can be most efficiently implemented in arrays with the Parent Nod (P) is floor(Child Node - 1 / 2).

#### Minimum Spanning Trees

##### Problem
> Suppose we wish to connect all the computers in a new office using the least amount of cable.  

* Can model this problem using weighted graph G whose V represent Comptuers and E which represents all possible pairs(u,v) of computers.
* Each edge has a weight (W) of w((u,v)) which is equal to the amount of cable needed to connect computer u,v
* We need to find a Tree **T** that contains all of the vertices of G and has the minimum total weight over all such trees.
* Tree **T** is an undirected Graph in which any two V are connected by exactly one path.
* Trees do not have any simple loops (uni-directional)
  * No loops , no parrallel edges


> More formally the problem definition is that we assume the input graph G is  
* Unidirected 
* No simple loops
* We denote the E of G as unordered pairs of V 
* Given a weighted undirected graph G we want to find a tree **T** that contains all V of G 

> More formally the tree T above is a **spanning** tree  (Spans entire graph)  
> A **minimum** spanning tree is a spanning tree wich minimizes the sum  
> W(T) = Sigma [bottom of Sigma] (u,v) in the set T with w((u,v)) . 

* Efficient algorithms (A) for MST pre-date compSci 
* Two classic algorithms , both are applications of the **greed** method.
* Kruskal's A which grows MST in clusters
* Prim-Jarnik algorithm , grows MST from single starting vertex. 

##### Crucial fact about MST
> let G be Weighted connected G , Vsub1 and Vsub2 be a partition of the V of G into two disjoin nonempty sets .  
>Furthermore , let e be an E of G with min Weight from the edges with one endpoint in Vsub1 and the other in Vsub2 .  
>There is a MST **T** that has e as one of it's edges.  

###### Justification
* Let T be MST of G 
* If T does not contain the edge e then it must contain another edge e' which has endpoint in V sub1 and the other in V sub2 .
* Moreover, by the choice of e we know that w(e) <= w(e') 
* If we remove e' from T U { e } then we obtain a spanning tree whose total weight is not more than before. 
* Since T was a MST , this new T is also a MST 


##### Kruskal's Algorithm.

* greedily builds MST in clusters
* Initially each V is in it's own cluster (C) .
* Each edge is then considered ordered by increasing weight
* If an edge e connects two different clusters, then e is added to the set of edges of the MST, and then two C's are merged into a single C. 
* else if e connects two V that are already in the same cluster then e is discarded
* Once enough edges are found to form a spanning tree, the (A) terminiates and outputs this as the MST. 

##### Kruskal's MST Algorithm

Input: Simple connected weighted graph G with n V and m E 

```
function Kruskal(G) 
  //Initialise Clusers  
  clusters = {}  
  for all v in V of G {  
    add {v} to clusters
  end for  
  //Init edge priority queue  
  es = priority queue  
  for all e in E of G  
    add e to es with key w(e) //sorting on w(e) the weighted value  
  end for  
  // Greedily build MST  
  MST = {}  
  while ( MST < n -1 edges ) {
    (u,v) = es.removeMin() //gives edge connecting u,v 
    C(v) = cluster.find(v) // return cluster containing v 
    C(u) = cluster.find(u) // return cluster containing u
    if(C(u) != C(v)) then 
      add (u,v) to MST 
      remove C(u) and C(V) from clusters
      add new Cluster(C(u),C(v)) to clusters. // add union of C(v) and C(u) back as one cluster. 
      end if
      }
      return MST
      end Kruskal function
  ```
#### The Prim-Jarnik (A) 

* grows MST from single cluster starting from some root vertex v.
* We begin with some v defining an initial cloud (CL) of vertices 
* Iterate , choose a min-weight edge e = (v,u) , connecting a vertex v in Cl to a vertex u outside of Cl.
* The vertex u is then brought into the Cl and process is repeated until MST is formed. 


* The crucial fact about MST comes into play : by always choosing the smallest weighted edge joining a Vertex inside Cl to one outside Cl , we are assured of always adding a valid edge to the MST
* To efficiently implement this approach , we maintain a number D[u] for each vertex u outside of Cl , so that D[u] stores the weight of the best current edge e for joining u to the Cloud CL. 
* These labels allow us to reduce the # of edges that we must consider in deciding which vertex is next to join the cloud Cl. 

```
Input: A simple connected weighted graph G with n V and m E  
Output: MST of G

function Prim-Jarnik(G)
  //select any vertex in G.
  D[v] = G.getVertex(0) //choose 0 
  priorityQueue PQ 
  for all vertices u except v in G { //since we already have v 
    D[u] = w((u,v)) //w((u,v)) = least weight cost edge connecting u,v 
    
    // add el u and edge (u,v) 
    add el [u,(u,v)] with key D[u] to priorityQueue 
    }
    // sort the PriorityQueue transferring el and edges (u,v) to MST 
    MST = {}
    while priorityQueue.notEmpty() {
      (u,e) = pq.removeMin()
      add(u,e) to MST
      for all(z, , _) in pq {
        if( w((u,z)) < D[z] then
          D[z] = w((u,z))
          change the element of (z,_) in Q to (z,(u,z))
          change the key of (z,_) in Q to D[z] 
        end if
      }
    }
    return MST 
    end function
  ```
  
  



  