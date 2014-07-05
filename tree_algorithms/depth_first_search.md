# Depth First Search

Depth First Search (or DFS for short) is the easier to implement algorithm for traversing a tree. The name comes from the fact that you dive deep into the tree from the beginning of the traversal. It is commonly used to see if a node exists in a given tree and usually starts from the head node. We'll take a look at what happens visually.

The pseudocode for DFS is as follows:
1. Do whatever to the node we want to do if it hasn't already been done
2. See if it has unvisited children
3. If it has unvisited children, visit the first unvisited child and start the pseudocode for the new node
4. If it doesn't have unvisited children, go to its parent and restart the pseudocode for the parent node
5. If it doesn't have a parent, you're done! (You're at the head node)

![DFS 0](http://imgur.com/aaln0Er.png)

The above is the tree structure we will be traversing. The number of children per node is variable, meaning that any node can have any number of children. Node A, the head node, has 3 children, B, C and D. Node B has only one child, E. Node M has no children. Let's say that we're wanting to traverse through the entire tree using depth first search. To do this, we're going to start at the head node, node A.

![DFS 1](http://i.imgur.com/ZKTsb0v.png)

Here we are at node A. The current node we are at will be highlighted **red**. In depth first search, we move to the current node we're on's children, until we've visited them all or the node has no children. We're going to move to node B, node A's child.

Nodes Visited: [A]

![DFS 2](http://i.imgur.com/U6ffvqg.png)

Here we are at node B. Visited nodes, such as node A, will be marked in yellow. Because we are currently at node B and we know that DFS wants to visit the current nodes children, we go on to node E, node B's child.

Nodes Visited: [A, B]

![DFS 3](http://i.imgur.com/IWFegZ4.png)

Now we're at node E. Node E has an unvisited child, node J, so we visit it.

Nodes Visited: [A, B, E]

![DFS 4](http://i.imgur.com/pFvPXpQ.png)

Node J is added to our list of visited nodes, but it has no children! What do we do now? We go back to its parent and see if it has any more children to visit. J's parent is node E. Node E has no more children to visit, so we move to its parent. E's parent is node B. Node B has no children left to visit, so we move to its parent, node A. Node A still has two children left to visit, so we'll move to node C.

Nodes Visited: [A, B, E, J]

![DFS 5](http://i.imgur.com/DCcjEXv.png)

At this point, the meaning behind the name Depth First Search becomes evident. You can see the algorithm dive deep into a single branch of the tree, down to the very bottom, before starting the next branch. In this case, the branch it dove deep into was all of the nodes that were a descendant of node B.

Node C is added to our visited list. It has children that haven't been visited, so we go to its child F.

Nodes Visited: [A, B, E, J, C]

![DFS 6](http://i.imgur.com/wZcQsva.png)

Node F is added to our visited list. It has one child, unvisited node K, so we go to node K.

Nodes Visited: [A, B, E, J, C, F]

![DFS 7](http://i.imgur.com/WpMgkvI.png)

Node K is added to our visited list. It has no children, so we go back to its parent, node F. Node F has no more children left to visit, so we go to its parent, node C. Node C has node G which hasn't been visited yet, so we go to node G.

Nodes Visited: [A, B, E, J, C, F, K]

![DFS 8](http://i.imgur.com/T2Lo8iB.png)

Node G is added to our visited nodes list. It has three children that haven't been visited yet, so we go to the first one, node L.

Nodes Visited: [A, B, E, J, C, F, K, G]

![DFS 9](http://i.imgur.com/Ha8tALc.png)

Node L is added to our visited nodes list. Node L has no children, so we go to its parent, node G. Node G has two children that haven't been visited yet, so we go to the first, node M.

Nodes Visited: [A, B, E, J, C, F, K, G, L]

![DFS 10](http://i.imgur.com/R9eHUB6.png)

Node M is added to our visited nodes list. Node M has no children, so we go to its parent, node G. Node G has one child that hasn't been visited yet, so we go to it, node N.

Nodes Visited: [A, B, E, J, C, F, K, G, L, M]

![DFS 11](http://i.imgur.com/7mALDWy.png)

Node N is added to our visited list. Node N has no children, so we go to it's parent, node G. Node G has no unvisited children, so we go to its parent, node C. Node C has one unvisited child, node H, so we go to node H.

Nodes Visited: [A, B, E, J, C, F, K, G, L, M, N]

![DFS 12](http://i.imgur.com/42XPCBn.png)

Node H is added to the visited list. Node H has one unvisited child, node O, so we go to node O.

Nodes Visited: [A, B, E, J, C, F, K, G, L, M, N, H]

![DFS 13](http://i.imgur.com/8vK6JSL.png)

Node O is added to the visited list. Node O has no children, so we go to its parent, node H. Node H has no unvisited children, so we go to its parent, node C. Node C has no unvisited children, so we go to its parent, node A. Node A has one unvisited child, node D, so we go to Node D.

Nodes Visited: [A, B, E, J, C, F, K, G, L, M, N, H, O]

![DFS 14](http://i.imgur.com/h8GqFS7.png)

Here we can see that we dove deep into two branches of the tree, the branches that have nodes that are descendants of node B or node C. Now we're diving into the final branch, those nodes that are a descendant of node D.

Node D is added to the visited nodes list. Node D has one unvisited child, node I, so we go to node I.

Nodes Visited: [A, B, E, J, C, F, K, G, L, M, N, H, O, D]

![DFS 15](http://i.imgur.com/C5v2Ej2.png)

Node I is added to the visited nodes list. Node I has one unvisited child, node P, so we got to node P.

Nodes Visited: [A, B, E, J, C, F, K, G, L, M, N, H, O, D, I]

![DFS 16](http://i.imgur.com/q9v4dNq.png)

Node P is added to the visited nodes list. Node P has no unvisited children, so we go to its parent, node I. Node I has no unvisited children, so we go to its parent, node D. Node D has no unvisited children, so we go to its parent, node A. Node A has no unvisited children and has no parent. We're done with our DFS!

Nodes Visited: [A, B, E, J, C, F, K, G, L, M, N, H, O, D, I, P]


## Exercises

Your job is to write a method that solves Depth First Search recursively.  Then, write a method that solves DFS iteratively. For each node, you should
