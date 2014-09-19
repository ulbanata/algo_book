# Building a Graph - The Node

```ruby
class Node
  attr_reader :value
  attr_accessor :connections

  def initialize(value)
    @value = value
    @connections = {}
  end
end
```

The node class is very similar to the nodes you've seen before for the tree and linked list classes. The node class contains the value that is being stored in the node and all the connections to other nodes the current node has.
