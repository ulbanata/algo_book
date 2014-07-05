# BFS Recursive Solution

```ruby
def bfs(node, queue=[])
  p node.value
  node.children.each do |child|
    queue.push(child)
  end
  bfs(queue.shift, queue) unless queue.empty?
end
```
