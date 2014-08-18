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

The iterative solution to depth first search is more involved than the recursive solution. In order to run the depth first search, a stack is needed. Remember that a stack is a Last-In, First-Out data structure. The last thing that was added is the first thing that is removed. Using a stack in this context means that whenever a node is removed from the stack, all of its children are then added. This results in visiting a node's children before visiting the same node's siblings, just like Depth First Search is supposed to work.
