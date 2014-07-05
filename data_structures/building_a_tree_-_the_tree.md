# Building a Tree - The Tree
We have our node class built, but how do we connect them? To be honest, you don't need much more than the node class to build out a tree. But it is a lot easier to manipulate and work with your tree if you use a tree holder class. We're going to build out an example of such a class.

```ruby
class Tree
  def initialize

  end
end
```

What do we need to track in our tree? The head of the tree is very important for most tree implementations. Knowing which node is the head of the tree allows us to traverse the tree from the very top.

```ruby
class Tree
  attr_reader :head

  def initialize
    @head = nil
  end
end
```

How do we add things to our tree? We'll need a method for that. Let's build one out!

```ruby
class Tree
  attr_reader :head

  def initialize
    @head = nil
  end

  def add_node(value, parent_node = nil)
    node = Node.new(value)
    parent_node.children << node if parent_node
    node.parent = parent_node if parent_node
    @head = node unless @head
    node
  end
end
```

So what does our add_node method do? It takes in two parameters, the value associated with the node and the parent node that the new node will be attached to (if there is one). It creates the node with the value, and then adds it as a child of the parent node. It then sets the parent of the new node to its parent. Finally, it checks to see if there is already a head node. If there isn't one, it assumes the current node is the first node being created and makes it the head node. It then returns the node that was created.

Now let's add a way to remove things from our tree.

```ruby
class Tree
  attr_reader :head

  def initialize
    @head = nil
  end

  def add_node(value, parent_node = nil)
    node = Node.new(value)
    parent_node.children << node if parent_node
    node.parent = parent_node if parent_node
    @head = node unless @head
    node
  end

  def remove_node(node)
    parent = node.parent
    parent.children.delete(node)
  end
end
```

Our delete method is simple enough, perhaps deceptively so. It allows you to remove an entire branch at once! Removing one node from the tree also removes all of its children. This can be very powerful, but also dangerous. Make sure you think about what you're wanting to do when writing out your remove_node method!

