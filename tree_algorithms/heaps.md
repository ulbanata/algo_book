# Heaps

While the Heap should belong in the array algorithms section, it only makes sense in the context of a Priority Queue. With the priority queue, you had to make sure that the tree stayed balanced. That meant, periodically, that you had to rebalance the tree, which takes O(n) time to complete. What if I told you that you could do the same thing the the priority queue did and shove it into an array data structure without increasing the runtime (And actually improving it by not having to rebalance!)?

Let's look back at the different commands we had for the priority queue. Removing an item from the PQ takes the last item in the tree and moves it to the top. In an array, this would be the same as copying the first item in the array, then popping out the last item and placing it as the first item in the array. Adding items to the PQ are akin to pushing an item to an array. Swapping items to keep the PQ in order can be mimicked in an array by swapping two elements' values like we did in most of the sorting algorithms.

The use of an array in the heap keeps the complexity at a minimum. You have to do a little math to figure out who is what's child or parent, but you no longer have to worry about keeping track of the number of children a side has to rebalance. Let's build out a heap from a PQ and see what it looks like.

![Heap Part 1](http://i.imgur.com/uIL9L9V.png)

We start by pushing the head to the array, so 78 is the first element in our array.

![Heap Part 2](http://i.imgur.com/LjLJJas.png)

We then push the head node's children to the array, in order. The left node is pushed first, followed by the right node. The first element in our array has its two children in the array as the second and third elements.

![Heap Part 3](http://i.imgur.com/CHOKngh.png)

59 is the next element in the array. We add its children to the array by pushing them on to the end.

![Heap Part 4](http://i.imgur.com/KUVFnhP.png)

65 is the next element in the array. We push its children to the array next. Now we have several parent/children groups added to the array. The head node has an index of 0. Its children have indices 1 and 2. Node 59 has an index of 1. Its children have indices of 3 and 4. Node 65 has an index of 2. Its children have indices of 5 and 6.

![Heap Part 5](http://i.imgur.com/tbcZYaw.png)

We continue the process by adding node 47's children to the array. This keeps happening until all of the remaining nodes have been pushed to the array by their parent.

![Heap Part 6](http://i.imgur.com/o9AvJLv.png)
![Heap Part 7](http://i.imgur.com/GNKxNmn.png)
![Heap Part 8](http://i.imgur.com/0oLRZSU.png)

Our heap is complete and now we don't have to worry about balancing! But how do we find a nodes parent and children? With math!

<table>
<tr>
    <th>n</th>
    <th>Child 1</th>
    <th>Child 2</th>
</tr>
<tr>
    <td>0</td>
    <td>1</td>
    <td>2</td>
</tr>
<tr>
    <td>1</td>
    <td>3</td>
    <td>4</td>
</tr>
<tr>
    <td>2</td>
    <td>5</td>
    <td>6</td>
</tr>
<tr>
    <td>3</td>
    <td>7</td>
    <td>8</td>
</tr>
<tr>
    <td>4</td>
    <td>9</td>
    <td>10</td>
</tr>
<tr>
    <td>5</td>
    <td>11</td>
    <td>12</td>
</tr>
<tr>
    <td>6</td>
    <td>13</td>
    <td>14</td>
</tr>
</table>

For each node n above, its two children can be found by the equations `2*n + 2` and `2*n + 1`. For **node 0**, its children are `2*0 + 2` and `2*0 + 1`, which reduces to **2** and **1**. For **node 5**, its children are `2*5 + 2` and `2*5 + 1`, which reduces to **12** and **11**. This works for all nodes in the heap. Check it out with the table above!

<table>
<tr>
    <th>n</th>
    <th>Parent</th>
</tr>
<tr>
    <td>1</td>
    <td>0</td>
</tr>
<tr>
    <td>2</td>
    <td>0</td>
</tr>
<tr>
    <td>3</td>
    <td>1</td>
</tr>
<tr>
    <td>4</td>
    <td>1</td>
</tr>
<tr>
    <td>5</td>
    <td>2</td>
</tr>
<tr>
    <td>6</td>
    <td>2</td>
</tr>
<tr>
    <td>7</td>
    <td>3</td>
</tr>
<tr>
    <td>8</td>
    <td>3</td>
</tr>
<tr>
    <td>9</td>
    <td>4</td>
</tr>
<tr>
    <td>10</td>
    <td>4</td>
</tr>
<tr>
    <td>11</td>
    <td>5</td>
</tr>
<tr>
    <td>12</td>
    <td>5</td>
</tr>
<tr>
    <td>13</td>
    <td>6</td>
</tr>
<tr>
    <td>14</td>
    <td>6</td>
</tr>
</table>

For each node, n, you can find its parent with the equation `(n-1)/2`. Remember in Ruby that dividing an integer with an integer will return an integer. For another language that will return a float, the equation would need to include a floor, like so: `((n-1)/2).floor`. Using this equation, **node 7's** parent is `(7-1)/2`, which reduces to **3**. **Node 88's** parent is `(88-1)/2`, which reduces to **44**. This works for any node in our heap except the head node (because the head node has no parent).
