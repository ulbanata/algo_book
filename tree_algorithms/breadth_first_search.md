# Breadth First Search

Breadth First Search (or BFS for short) is the easier to understand, but more difficult to code, tree traversal algorithm. This algorithm looks through each layer of a tree at a time.

The pseudocode for BFS:
1. Do whatever to the node we want to do if it hasn't already been done
2. Add any children it has to a queue
3. If there is no node left in the queue, exit the BFS, you're done!
3. Otherwise, remove the next node from the queue and start the pseudocode over for the node removed from the queue

![BFS 0](http://imgur.com/aaln0Er.png)

We'll use the same tree as we used in the DFS algorithm. Once again, we start with the head node, node A.

![BFS 1](http://i.imgur.com/ZzqNHiB.png)

We add node A to the visited nodes list. We add all of its children to the queue. The first node in the queue is removed and we go to that node, node B.

Nodes Visited: [A]

Queue: [C, D]

Next Node: B

![BFS 2](http://i.imgur.com/crHB8ac.png)

We add node B to the visited nodes list. We add node B's child, node E, to the queue. The next node in the queue is removed and we go to that node, node C.

Nodes Visited: [A, B]

Queue: [D, E]

Next Node: C

![BFS 3](http://i.imgur.com/6Nm4LMa.png)

We add node C to the visited nodes list. We add node C's children, nodes F, G and H, to the queue. The next node in the queue is removed and we go to that node, node D.

Nodes Visited: [A, B, C]

Queue: [E, F, G, H]

Next Node: D

![BFS 4](http://i.imgur.com/URGVplz.png)

At this point, we can visualize why this algorithm is called Breadth First Search. Instead of diving deep into a branch, as in the Depth First Search algorithm, we traverse through each layer. So far, we have traversed through layers 1 and 2. Layer 1 contained node A and layer 2 contained nodes B, C, and D. You can also see that this algorithm will visit the nodes in a way that makes it print out the alphabet. This continues until we've gone through all of the nodes.

We add node D to the visited nodes list. We add node D's child, node I, to the queue. The next node in the queue is removed and we go to that node, node E.

Nodes Visited: [A, B, C, D]

Queue: [F, G, H, I]

Next Node: E

![BFS 5](http://i.imgur.com/SdQFbxo.png)

We add node E to the visited nodes list. We add node E's child, node J, to the queue. The next node in the queue is removed and we go to that node, node F.

Nodes Visited: [A, B, C, D, E]

Queue: [G, H, I, J]

Next Node: F

![BFS 6](http://i.imgur.com/XPpAkro.png)

We add node F to the visited nodes list. We add node F's child, node K, to the queue. The next node in the queue is removed and we go to that node, node G.

Nodes Visited: [A, B, C, D, E, F]

Queue: [H, I, J, K]

Next Node: G

![BFS 7](http://i.imgur.com/ThdUCOp.png)

We add node G to the visited nodes list. We add node G's children, nodes L, M, and N, to the queue. The next node in the queue is removed and we go to that node, node H.

Nodes Visited: [A, B, C, D, E, F, G]

Queue: [I, J, K, L, M, N]

Next Node: H

![BFS 8](http://i.imgur.com/DySIRZa.png)

We add node H to the visited nodes list. We add node H's child, node O, to the queue. The next node in the queue is removed and we go to that node, node I.

Nodes Visited: [A, B, C, D, E, F, G, H]

Queue: [J, K, L, M, N, O]

Next Node: I

![BFS 9](http://i.imgur.com/DiJ3UVO.png)

At this point, the remaining nodes have no children left. The queue will continue to shrink until no nodes remain and we complete the BFS.

We add node I to the visited nodes list. We add node I's child, node P, to the queue. The next node in the queue is removed and we go to that node, node J.

Nodes Visited: [A, B, C, D, E, F, G, H, I]

Queue: [K, L, M, N, O, P]

Next Node: J

![BFS 10](http://i.imgur.com/00dSSq8.png)

We add node J to the visited nodes list. Node J has no children, so no nodes are added to the queue. The next node in the queue is removed and we go to that node, node K.

Nodes Visited: [A, B, C, D, E, F, G, H, I, J]

Queue: [L, M, N, O, P]

Next Node: K

![BFS 11](http://i.imgur.com/tLjV9hf.png)

We add node K to the visited nodes list. Node K has no children, so no nodes are added to the queue. The next node in the queue is removed and we go to that node, node L.

Nodes Visited: [A, B, C, D, E, F, G, H, I, J, K]

Queue: [M, N, O, P]

Next Node: L

![BFS 12](http://i.imgur.com/iKm7d4i.png)

We add node L to the visited nodes list. Node L has no children, so no nodes are added to the queue. The next node in the queue is removed and we go to that node, node M.

Nodes Visited: [A, B, C, D, E, F, G, H, I, J, K, L]

Queue: [N, O, P]

Next Node: M

![BFS 13](http://i.imgur.com/PMVuxIw.png)

We add node M to the visited nodes list. Node M has no children, so no nodes are added to the queue. The next node in the queue is removed and we go to that node, node N.

Nodes Visited: [A, B, C, D, E, F, G, H, I, J, K, L, M]

Queue: [O, P]

Next Node: N

![BFS 14](http://i.imgur.com/WCKYvzc.png)

We add node N to the visited nodes list. Node N has no children, so no nodes are added to the queue. The next node in the queue is removed and we go to that node, node O.

Nodes Visited: [A, B, C, D, E, F, G, H, I, J, K, L, M, N]

Queue: [P]

Next Node: O

![BFS 15](http://i.imgur.com/oGFElU7.png)

We add node O to the visited nodes list. Node O has no children, so no nodes are added to the queue. The next node in the queue is removed and we go to that node, node P.

Nodes Visited: [A, B, C, D, E, F, G, H, I, J, K, L, M, N, O]

Queue: []

Next Node: P

![BFS 16](http://i.imgur.com/juV5gvZ.png)

We add node P to the visited nodes list. Node P has no children, so no nodes are added to the queue. The queue is empty, so we exit the algorithm. Our Breadth First Search of the tree is complete!

Nodes Visited: [A, B, C, D, E, F, G, H, I, J, K, L, M, N, O, P]

Queue: []

Next Node: nil

