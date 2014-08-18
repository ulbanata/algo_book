# Pre-Order

```ruby
def pre_order(node)
  stack = Stack.new
  stack.push(node)
  while stack.peek
    node = stack.pop
    p node.value
    stack.push(node.right_child) if node.right_child
    stack.push(node.left_child) if node.left_child
  end
end
```

The iterative pre-order printing solution is a bit more in-depth than its recursive counterpart. In order to keep track of which node should be printed next, a stack is used. Just like the recursive pre-order printing solution was the same as the recursive depth first search, the iterative pre-order printing solution is the same as the iterative depth first search!

