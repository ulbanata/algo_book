# DFS Recursive Solution

```ruby
def dfs(node)
  p node.value
  node.children.each do |child|
    dfs(child)
  end
end
```

The method above is a recursive solution for depth first search of a tree. To run the method, you can toss in any node initially. I started with the head. The method prints the value of the current node and then calls dfs and passes in each of its children.
