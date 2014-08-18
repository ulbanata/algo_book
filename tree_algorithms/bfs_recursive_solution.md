# BFS Recursive Solution

```ruby
def bfs(node, queue=Queue.new)
  p node.value
  node.children.each do |child|
    queue.push(child)
  end
  bfs(queue.shift, queue) if queue.peek
end
```

The recursive solution for breadth first search is more complicated than the depth first search solution. This is due to the fact that a queue is needed to keep track of the order the nodes should be ran in. The queue is a First-In, First-Out data structure, meaning that whenever a node is removed from a queue, the node's siblings will be used before the node's children. <!-- Need to improve wording here -->
