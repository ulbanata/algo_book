# Priority Queues

It's your job in a company to determine what job request to run next after the first is completed. All of the jobs have different rankings of importance, 1 - 10, where 10 is the most important. You can get a new job request at any time and someone can complete a task at any time. For a small number of jobs, you can easily keep track of which one needs to be done. But this is a big company, they can have thousands of jobs in a day! How can you keep track of them all efficiently using a data structure? None of the data structures we've covered so far will efficiently keep the jobs in an order where you can give someone a new job or take in a new job order quickly. That's where priority queues come in.

A priority queue, or pq for short, is a data structure very similar to a queue. You can add items to the priority queue and remove the next item to be completed, just like in a queue. The difference is how the two data structures determine which item should be removed. A queue will remove the next item based on how long its been in the queue. The item that has been in the queue the longest will be the one removed from the queue. It is the first in line. For the priority queue, each item that is added to the list has a value. The item with the highest (or lowest) value in the priority queue is what is removed and returned. In our task manager example above, the value being tracked was job priority. A job with a priority of 10 would be the item that was returned by the priority queue, even if it had just been added.

The internal structure of a priority queue is a balanced binary tree (BBT). The BBT has the standard rules:
1. A node can have 0, 1, or 2 children. (Binary rule)
2. All leaves must be within log<sub>2</sub>(n) or log<sub>2</sub>(n) - 1 level of the tree. (Balanced rule)

The new rule that the priority queue enforces on its tree is that **each node must be larger (or smaller, depending on the type of priority) than its children**. Below is an example of a priority queue that is returning the maximum number in a sequence of numbers.

![PQ](http://i.imgur.com/Cp4K69d.png)

You can see that the largest number in the tree, 78, is at the head of the tree. The head is the node that will be removed whenever you need to call **.shift** on the priority queue.

Any node that you look at within the tree follows the priority queue rule. It is larger than its children. You might notice that 62 is further down on the tree than 59 is. 62 is on level 3 while 59 is on level 2. This might seem counterintuitive at first. If we're supposed to remove the biggest item from the tree, wouldn't it make sense to have the largest items in the tree nearest the head? However, as you'll soon see, the rule that a node must be smaller than its children is the only new rule that is needed to get the full functionality of the priority queue. Making sure the largest items are at the top of the tree would actually slowdown the runtime of the priority queue!

## PQ.shift

Here are the steps to remove an item from the priority queue.

![PQ Remove Item Part 1](http://i.imgur.com/djvr7yM.png)

We know that we are removing the head node, so we take its value and return it. In this case, that is the value 78.

![PQ Remove Item Part 2](http://i.imgur.com/P4iPAVl.png)

78 is removed from the tree, but we need to update our priority queue so that the next largest item is at the top of our tree. How can we do this? Can we just grab the largest item in the tree and move it there? We could if we knew what it was! But in order to do that, we would have to search through the entire tree. The answer might sound a little counter-intutitive.

![PQ Remove Item Part 3](http://i.imgur.com/7DvLpcQ.png)

We're going to take an item from the lowest level and move it to the head position! This is the start of a process called **bubble down**. We're going to grab the number 19 from the lowest level of the tree and bubble down the tree to update it.

![PQ Remove Item Part 4](http://i.imgur.com/k56Pw08.png)

19 is now the head node. You will notice that this current configuration is breaking the rule of the priority queue, the children are larger than the parent! We need to do something about this.

![PQ Remove Item Part 5](http://i.imgur.com/VsgmFQ8.png)

In order to see what item should be at the head of our priority queue, we're going to compare the head node and its two children. If the head node is larger than its children, then we don't need to do anything, and our bubble down ends. If the largest node is one of the children, we need to swap the largest child node with the head node.

![PQ Remove Item Part 6](http://i.imgur.com/cuhfXJO.png)

65 is the largest node out of the three that we are comparing, so we will swap 19 and 65.

![PQ Remove Item Part 7](http://i.imgur.com/o3Rh1fW.png)

The head node is now the largest node in the tree! But are we done with our bubble down? Not yet, 19 is still smaller than its children!

![PQ Remove Item Part 8](http://i.imgur.com/74O6vb9.png)

We compare 19 to its children, 62 and 38, to determine which is the largest node.

![PQ Remove Item Part 9](http://i.imgur.com/GCmVWYL.png)

62 is the largest node out of the three, so we will swap 19 and 62.

![PQ Remove Item Part 10](http://i.imgur.com/mLiQhEd.png)

The nodes have been swapped. We need to compare 19 to its two new children to see if we need to continue running our bubble down.

![PQ Remove Item Part 11](http://i.imgur.com/OaVqRi8.png)

We compare the nodes 19, 21, and 43 to see which is largest.

![PQ Remove Item Part 12](http://i.imgur.com/IrrkpT1.png)

Node 43 is the largest of the three nodes, so it and 19 will be swapped with 43.

![PQ Remove Item Part 13](http://i.imgur.com/Q5B6yNS.png)

19 doesn't have any children, so we can end our bubble down at this point.
