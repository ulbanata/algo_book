# BFS Recursive Solution

```ruby
def bfs(node, queue=Queue.new)
  p node.value
  node.children.each do |child|
    queue.push(child)
  end
  bfs(queue.shift, queue) if queue.peak
end
```
