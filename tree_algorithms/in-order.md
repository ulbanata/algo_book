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
