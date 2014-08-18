# Recursive Solutions

The recursive solutions for printing binary trees are shorter and less verbose than the iterative solutions. The important thing to remember here is that we are doing a depth first search and the location of the puts statement determines what kind of order the tree will be printed in.

In-Order:
```ruby
def in_order(node)
  in_order(node.left_child) if node.left_child
  puts node.value
  in_order(node.right_child) if node.right_child
end
```

In-order printing is the most common. Going back to the binary tree search, the method we used to rebalance the tree was actually an in-order print. It retrives the numbers of a binary search tree from smallest to largest.

Pre-Order:
```ruby
def pre_order(node)
  puts node.value
  pre_order(node.left_child) if node.left_child
  pre_order(node.right_child) if node.right_child
end
```

The pre-order printing method is the same as the in-order except the puts statement is the first line in the method, before the children are visited. Also note that the pre-order solution is the same thing as a depth first search of the tree. Look back to the Depth First Search Recursive Solution to see what I'm talking about!

Post-Order:
```ruby
def post_order(node)
  post_order(node.left_child) if node.left_child
  post_order(node.right_child) if node.right_child
  puts node.value
end
```

The post-order printing method has the puts statement at the end of the method, after the children have been visited.
