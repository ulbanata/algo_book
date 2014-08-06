# DFS Iterative Solution

```ruby
def dfs(start_node)
  stack = Stack.new
  stack.push(start_node)
  while stack.peak
    node = stack.pop
    p node.value
    node.children.each do |child|
      stack.push(child)
    end
  end
end
```

The iterative solution to depth first search is more involved than the recursive solution. In order to run the depth first search, a stack is needed. I loop through the stack until its empty, printing each value and adding any of the current node's children to the stack.
