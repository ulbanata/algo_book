# Recursive Solutions

In-Order:
```ruby
def in_order(node)
  in_order(node.left_child) if node.left_child
  puts node.value
  in_order(node.right_child) if node.right_child
end
```

Pre-Order:
```ruby
def pre_order(node)
  puts node.value
  pre_order(node.left_child) if node.left_child
  pre_order(node.right_child) if node.right_child
end
```

Post-Order:
```ruby
def post_order(node)
  post_order(node.left_child) if node.left_child
  post_order(node.right_child) if node.right_child
  puts node.value
end
```
