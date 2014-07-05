# Printing Binary Trees

A very common interview question pertains to printing out binary trees. There are three ways to print out a BT: in-order, pre-order and post-order. We'll use the same binary tree as we did for binary search trees.

![](http://i.imgur.com/FM8IOKo.png)

Here is what our methods might look like when ran:

```
:001 > BST.in_order
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
 => nil
```

For a binary search tree, this method prints out the numbers in order.

```
:002 > BST.pre_order
8
4
2
1
3
6
5
7
12
10
9
11
14
13
15
 => nil
```

These are the numbers of our BST printed out in pre-order.

```
:003 > BST.post_order
1
3
2
5
7
6
4
9
11
10
13
15
14
12
8
 => nil
```

And our BST printed out in post-order.
