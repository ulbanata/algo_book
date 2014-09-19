# Building a Graph - The Graph

```ruby
class Graph
  attr_reader :nodes

  def initialize
    @nodes = {}
  end

  # Adding/removing nodes

  def add_node(value)
    @nodes[value] = Node.new(value)
  end

  def delete_node(node)
    node.connections.each do |connected_node, weight|
      remove_connection(node, connected_node)
    end
    @nodes.delete(node.value)
  end

  # Adding/removing Connections

  def connect_nodes(node1, node2, weight=0)
    node1.connections[node2] = weight
    node2.connections[node1] = weight
  end

  def remove_connection(node1, node2)
    node1.connections.delete(node2)
    node2.connections.delete(node1)
  end

  # Useful methods

  def adjacent?(node1, node2)
    return true if node1.connections[node2]
    false
  end

  def neighbors(node)
    node.connections.keys map { |node, weight| node }
  end

  def get_weight(node1, node2)
    return nil unless adjacent?(node1, node2)
    node1.connections[node2]
  end
end
```

We'll start breaking down the graph class with the `add_node` and `connect_nodes` methods.

```ruby
  def add_node(value)
    @nodes[value] = Node.new(value)
  end
```

The `add_node` method takes in a value as a parameter. It then creates a node and saves it to the `@node` instance variable. Notice that the node can be created without connecting it to anything! Unlike in a tree, a graph can have nodes that are not connected to anything else.

```ruby
  def connect_nodes(node1, node2, weight=0)
    node1.connections[node2] = weight
    node2.connections[node1] = weight
  end
```

The `connect_nodes` method takes two mandatory parameters and one optional parameter. The two mandatory parameters are the nodes that are being connected. The optional parameter is the weight of that connection. There are data sets that are best modelled as a graph with weights inbetween the nodes, such as maps (where the weight is the distance between nodes). There are also data sets that are best modelled as a graph where no weight is needed, such as friend connections on facebook (where each connection could be assumed to have the same weight, meaning that the connection weight doesn't need to be tracked). This class allows for both types of data structures to be modelled. The connections are created by saving the nodes in each other's `connections` hash, where the node that is being connected to is the key and the weight is the value.

Now that we can add and connect nodes, let's take a look at how to disconnect and delete them.

```ruby
  def remove_connection(node1, node2)
    node1.connections.delete(node2)
    node2.connections.delete(node1)
  end
```

The `remove_connection` method is very similar to the `connect_nodes` method. It takes in two parameters, the two nodes that are being disconnected. Each node's connection to the other node is removed using the hash `delete` method, which takes in the key of the hash and deletes the key/value pair from the hash.

```ruby
  def delete_node(node)
    node.connections.each do |connected_node, weight|
      remove_connection(node, connected_node)
    end
    @nodes.delete(node.value)
  end
```

The `delete_node` method takes the node that is being deleted and calls the `remove_connection` method on each connection the node has. Once all of the connections have been severed, the node itself is removed from the `@nodes` instance variable usind the hash `delete` method again. This effectively removes all traces of the node from the graph.

There are several useful methods that might be useful in different applications. We'll go over each of them.

```ruby
  def adjacent?(node1, node2)
    return true if node1.connections[node2]
    false
  end
```

The `adjacent?` method sees if two nodes are connected to each other. If they are, the method returns true. Otherwise, it will return false. This method determines if the two nodes are connected by seeing if node1's connections has a key/value pair for node2.

```ruby
  def neighbors(node)
    node.connections.keys
  end
```

The `neighbors` method returns an array of all of the nodes that are connected to a given node. This is done by calling the `keys` method on the `node.connections` hash.

```ruby
  def get_weight(node1, node2)
    return nil unless adjacent?(node1, node2)
    node1.connections[node2]
  end
```

The `get_weight` method takes two nodes as parameters and returns the weight of their connection, if they are connected. The `return nil` line will return nil if the nodes are not connected. Otherwise, it returns the weight of the connection through node1's connections hash.
