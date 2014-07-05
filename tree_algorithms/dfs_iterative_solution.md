# DFS Iterative Solution

```ruby
def dfs(node)
  stack = []
  stack.push(node)
  while !stack.empty?
    node = stack.pop
    p node.value
    node.children.each do |child|
      stack.push(child)
    end
  end
end
```

The iterative solution to depth first search is more involved than the recursive solution. In order to run the depth first search, a stack is needed. In this case, I used an array that I push nodes to and pop when I need another node. I loop through the stack until its empty.
