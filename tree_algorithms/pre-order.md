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


