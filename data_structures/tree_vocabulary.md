# Tree Terminology

![Node](http://i.imgur.com/MMrQwU5.png)

Each circle in the tree example above is a node. Nodes are the basic building blocks of trees. Each node holds information about itself and possibly knowledge on the other nodes it is connected to.

![Basic Tree](http://i.imgur.com/Z5lnK4n.png)

Here is a basic tree. You can see that we have 5 nodes in our tree. Those nodes are connected to each other by edges.

![Head of the Tree](http://i.imgur.com/TNi9z9H.png)

The node on top of the tree is called the Head node. It is important because, in order to traverse (move around) the tree, you usually start from the head.

![Tree Levels](http://i.imgur.com/8ug5dA8.png)

The tree is broken up into levels, with the top level being numbered 1 and incrementally increasing per level. You cannot skip levels! Nodes in level 2 can only be connected to nodes in level 1 and level 3. Nodes in level 1 can only be connected to nodes in level 2.

![Family Tree](http://i.imgur.com/mO899eQ.png)

Here you can see the family relationships for the blue node. The current node's Parent is the node one level above the current node (in Level 1) that is connected to it. A node can only have 1 parent!

The current node's Children are the nodes one level below the current node that are connected to it. For this example, the highlighted node is in level 2 and the highlighted node's children are in level 3. There is no limit to how many children a node can have in a standard tree data structure. However, there are certain trees that put a limit on the number of children a node can have. Binary trees are one such example, and they only allow 2 children per parent.

The current node's Siblings are any nodes that share the same parent as the current node. This also means that all sibling nodes are in the same level, but not all nodes in a level are siblings. (in this case, Level 2).
