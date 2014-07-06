# Post-Order

```ruby
def in_order(node)
  p_stack = Stack.new
  r_stack = Stack.new
  next = node
  while r_stack.peek || next || p_stack.peek
    if next
      if next.right_child
        r_stack.push(next)
      else
        p_stack.push(next)
      end
      next = next.left_child
    elsif p_stack.peek
      node = p_stack.pop
      p node.value
    else
      node = r_stack.pop
      next = node.right_child
      p_stack.push(node)
    end
  end
end
```

```ruby
def in_order(node)
  stack = Stack.new
  prev = node
  stack.push(node)
  while stack.peek
    node = stack.peek
    if prev.left_child == node || prev.right_child == node
      if node.left
        stack.push(node.left)
      elsif node.right
        stack.push(node.right)
      else
        p node.value
        stack.pop
      end
    elsif node.left == prev
      if node.right
        stack.push(node.rigth)
      else
        p node.value
    else
      p node.value
    end
  end
end
```


p_stack
child_stack
