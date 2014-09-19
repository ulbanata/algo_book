# In-Order

```ruby
def in_order(node)
  stack = Stack.new
  next = node
  while stack.peek || next
    if next
      stack.push(next)
      next = next.left_child
    else
      node = stack.pop
      p node.value
      next = next.right_child
    end
  end
end
```

The iterative in-order printing is even more complicated than the iterative pre-order printing. It contains two variables to store potential nodes to be printed, `next`, which contains a single node, and `stack`, which contains nodes to print in a stack. The `next` variable has precedence over the `stack` nodes. If there is a `next` node, then it is used first. We'll break down exactly how this works:

```ruby
  next = node
  while stack.peek || next
    if next
      stack.push(next)
      next = next.left_child
    else
      node = stack.pop
      p node.value
      next = next.right_child
    end
  end
```

`next` is first set as the head node. From here, we will go down the left child of each node. If it exists, the parent is pushed to the stack and the `next` variable is set as the left child of the parent node. If the left child doesn't exist, `next` is set to nil. If `next` is nil, then the `else` section of the if statement is invoked. When this occurs, the node at the top of the stack is popped out. This node is printed and this node's right child is set as the variable `next`'s value.

To better understand the code, build out a binary search tree and run through the recursive in_order method. <!-- Add images here? -->
