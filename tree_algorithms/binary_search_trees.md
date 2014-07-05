# Binary Search Trees

In the array algorithms section, we covered binary search. This search allowed us to find out if an item existed in the array in O(log(n)) time, which is a marked improvement over the O(n) runtime for a .include? method. This is great for static data that does not need to add or remove things to the sorted array. But what happens if you have a dynamic set of data? What if your data comes in randomly and you need to be able to search at any time? Adding or removing an element in an array has an O(n) runtime, which is not optimal. One way we can improve this is through the use of a specialized binary tree called a binary search tree.

In the tree data structure section, we went over the rules of a binary tree. It can only have 0, 1 or 2 children per node. Traditionally, the children are called the **left** or the **right** child. For a binary search tree, we add on an extra rule: **All children to the left of a node must be smaller than the node and all children to the right of a node must be larger than the node.**

Using the binary tree structure and the added rule for a binary search tree, we can build out a binary tree that allows us to perform the binary search just like we did it for an array structure. Let's convert a sorted array into a binary search tree and see what that looks like:

![Building a BBST Part 1](http://i.imgur.com/aQZj64n.png)

Here is the sorted array we will be converting over to a Binary Search Tree. It is a sorted array of numbers from 1 to 15. We're going to start with the middle of the array like we do for a binary search. The number 8 is in the middle of the array. This is the value we will place as the head node of our BST.

![Building a BBST Part 2](http://i.imgur.com/wT5ShoX.png)

We've added 8 as the head of our tree. Like binary search, we can break the array into two parts, the array that is left of 8 and the array that is right of 8. We'll start with the left array first. This array has 7 elements. We'll take the middle element and place it to the left of 8.

You'll notice that all of the elements to the left of 8 already satisfy the rule of binary search trees. Every element to the left of 8 is smaller than 8. Using a sorted array allows us to know that any element we add in our left array will fulfill the requirement that it is smaller than 8.

The middle element of the left array is 4, so we'll add 4 as 8's left child.

![Building a BBST Part 3](http://i.imgur.com/2BhTPWl.png)

The element 4 has been added to the BST. We can continue the process to add 4's children. Taking 4 splits the left array into two parts, left<sub>4</sub> and right<sub>4</sub>. We can take the middle array of left<sub>4</sub>, which is 2, and make it 4's left child.

![Building a BBST Part 4](http://i.imgur.com/XpTR5Xf.png)

2 is added as the left child of 4. 2 is smaller than 4, so the BST rules are satisfied.

4 also has a right child, the midpoint of right<sub>4</sub>, which is 6.

![Building a BBST Part 5](http://i.imgur.com/WmWlAZG.png)

6 is added as the right child of 4. 6 is larger than 4, so the BST rules are satisfied.

Now we need to add in 1, 3, 5, and 7 as a descendant of 4. We know that 1 is smaller than 4, so it goes to the left of 4. We also know that 1 is smaller than 2, so it goes to the left of 2.

![Building a BBST Part 6](http://i.imgur.com/WWfXeLU.png)

1 is added to the left of 2. 1 is smaller than all of its ancestors, so the BST rules are satisfied.

3 is smaller than 4, so it goes to the left of 4. 3 is larger than 2, so it goes to the right of 2.

![Building a BBST Part 7](http://i.imgur.com/yMrtbzP.png)

3 is added as the right child of 3. 3 is larger than 2, and smaller than 4 and 8. 3's location satisfies the BST rules.

5 is the next number to add to the tree. 5 is larger than 4, so it goes to the right of 4. 5 is smaller, so it goes to the left of 6.

![Building a BBST Part 8](http://i.imgur.com/02UrWxj.png)

5 is added as 6's left child. 5 is smaller than 6, larger than 4, but smaller than 8. 5 satisfies the BST rules.

Finally, we have 7 left to take care of the left<sub>8</sub> array. 7 is larger than 4, so it goes to 4's right. 7 is larger than 6, so it goes to 6's right.

![Building a BBST Part 9](http://i.imgur.com/Pht4pFA.png)

7 is added as the right child of 6. 7 is larger than 6 and 4 and smaller than 8, so 7's location satisfies the BST requirements.

Now let's start working on the right<sub>8</sub> array. We can take the midpoint of this array, which is 12. 12 is larger than 8, so we add it to 8's right.

![Building a BBST Part 10](http://i.imgur.com/qs6mWe1.png)

12 is added as 8's right child. 12 is larger than 8, so the BST rules are satisfied.

Once again, we can break an array in half. We now have a right<sub>12</sub> array, consisting of 9, 10, and 11. We also have a left<sub>12</sub> array, consisting of 13, 14, and 15. We can add the midpoint of the left array, 10, to the BST. 10 is larger than 8, so it goest to 8's right. 10 is smaller than 12, so it goes to 12's left.

![Building a BBST Part 11](http://i.imgur.com/KQwCTzH.png)

10 is added as 12's left child. 10 is smaller than 12 and larger than 8, so 10's location satisifies the BST rules.

We can add the right<sub>12</sub> midpoint to the array next. The midpoint is 14, which is larger than 8, so it goes to 8's right. 14 is also larger than 12, so it goes to 12's right.

![Building a BBST Part 12](http://i.imgur.com/h1gwzfR.png)

14 is added as 12's right child. 14 is larger than both 8 and 12, so its location fulfills the BST rules.

Continuing on with the remaining elements, 9, 11, 13, and 15, we can build out our BST.

![Building a BBST Part 13](http://i.imgur.com/qDUqPmA.png)
![Building a BBST Part 14](http://i.imgur.com/ByWRKor.png)
![Building a BBST Part 15](http://i.imgur.com/lwtKIo3.png)
![Building a BBST Part 16](http://i.imgur.com/FM8IOKo.png)

We've got a Binary Search Tree! Let's look at what happens when we look for 5 in our BST. We'll also show the standard binary search in our sorted array. Here is the pseudocode for searching for a value in a BST:
1. Start at the head.
2. If the node is what you are looking for, return true.
3. Otherwise, see if the value you are searching for is larger or smaller than the current nodes value.
4. If the value you are looking for is larger than the current node's value, go to the right child of the node. If there is no right node, return false.
5. Otherwise, go to the left child of the node. If there is no left child, return false.
6. Go to step 2 and repeat.

![Binary Search for 5 in BBST Part 1](http://i.imgur.com/tNPxHfS.png)

We start searching at 8, which is the head of the tree. The value we are searching for, 5, is not the same as the node we are on. 5 is smaller than 8, so we go to 8's left child.

For the binary search, we start at the midpoint of the array. 5 does not equal the midpoint, 8, so go to the midpoint of the left array of 8.

![Binary Search for 5 in BBST Part 2](http://i.imgur.com/CUKD65r.png)

Here, the similarity of the binary search tree and the binary search of the array is evident. The search of the BST has nullified all of the children to the right of 8, while the binary search has made it to where we don't need to search any elements to the right of 8 in the array.

We go back to line 2 in the pseudocode and start comparing values again. The number we are searching for, 5, is not equal to 4. 5 is greater than 4 so we go to 4's right child.

In the binary search, 5 is greater than 4, so we go to the midpoint of the new array we just created.

![Binary Search for 5 in BBST Part 3](http://i.imgur.com/ipmwrXr.png)

The tree and the array have the same number of nodes/elements left to search to find the number 5. The current node we are at has a value of 6, which isn't equal to 5. 5 is smaller than 6, so we go to 6's left child.

In the binary search, 5 is less than 6, so we go to the midpoint of the new array we just created, which has only 1 element.

![Binary Search for 5 in BBST Part 4](http://i.imgur.com/J9lVCpm.png)

We finally have our answer. The number we are searching for, 5, is equal to the value stored in the node, 5. We return true and exit out of our binary search of the BST.

The binary search of the array also sees that 5 == 5, returns true and exits out of the binary search.

That wasn't too bad! The time it took to run binary search on both our sorted array and our BST was the same amount of time. The runtimes of both algorithms when searching is still O(log(n)).

But let's take a look back at the rules for a binary search tree. Does the BST below break any of those rules?

![Unbalance BST](http://i.imgur.com/hqGA9GD.png)

No! The BST is not breaking any of our binary search tree rules. There is no node that has more than 2 children and all descendant values that are larger than the current node are to the right and all descendant values smaller are to the left. It's still a binary search tree, but it doesn't look too efficient. So how long would it take to search for 5 in this BST? Let's run through:

![Unbalanced Binary Search Tree Search for 5 Part 1](http://i.imgur.com/lDSR1VL.png)

5 is larger than 1, so we go to 1's right child.

![Unbalanced Binary Search Tree Search for 5 Part 2](http://i.imgur.com/9qKfXgc.png)

5 is larger than 2, so we go to 2's right child.

![Unbalanced Binary Search Tree Search for 5 Part 3](http://i.imgur.com/HwQ1gpr.png)

5 is larger than 3, so we go to 3's right child.

![Unbalanced Binary Search Tree Search for 5 Part 4](http://i.imgur.com/HcBB6UU.png)

5 is larger than 4, so we go to 4's right child.

![Unbalanced Binary Search Tree Search for 5 Part 5](http://i.imgur.com/xAj1w4L.png)

5 == 5, true!

This took a total of 5 steps, which is slower than the earlier BST we used! What gives? Aren't BST's supposed to have the same run time as a binary search in an array?

For a BST like the one we just used, the worst runtime we could expect would be O(n), if we searched for 15. For our earlier tree, the worst runtime would have been O(log(n)). The difference is that for the second tree, we have just a binary search tree. The first tree we worked with was a **balanced** binary search tree. A balanced binary search tree has another set of rules that we have to include in order to make sure it has a max runtime of O(log(n)). The max layer of the tree has to be at the ceiling of log(n)! This means that the max layer that we could have had for our BST was log(15).ceil => 4. The second BST we worked with had its max layer of 15!

So is all lost? Why would we ever use a BST instead of an array for a binary search? As we stated earlier, a BST is great if we might be adding items to be searched through at any point. We can add items to a BST much faster, in O(log(n)), than we could have in our array, in O(n). But if the search can take O(n) time for a BST, then what's the point?

We just saw that we can build a balanced binary search tree, and, in two chapters, we'll show how easy it can be to rebalance a binary search tree to make it a balanced binary search tree.
