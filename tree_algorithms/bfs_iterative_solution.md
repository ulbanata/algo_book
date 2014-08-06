# BFS Iterative Solution

```ruby
def bfs(start_node)
  queue = Queue.new
  queue.push(start_node)
  while queue.peak
    node = queue.shift
    p node.value
    node.children.each do |child|
      queue.push(child)
    end
  end
end
```

The above is an iterative solution for Breadth First Search. This method also uses a queue, just like the
recursive solution does. Notice that this solution is **identical** to the Iterative Depth First Search except that the BFS uses a **Queue** instead of a **Stack!** The only thing that changes which way you traverse through the tree is what data structure you hold your nodes in!


