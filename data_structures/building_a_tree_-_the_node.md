# Building a Tree - The Node

Because Ruby doesn't have a built in Tree class, we're going to build one. Just like we did with the Queue we built out, we're going to use two different classes to make it easier to code. First, we'll start with the node class, the basic building block of a tree.

What all information does our node class need to contain? Perhaps the most important one is the value associated with each node. The value can correspond to html tag in our DOM, the folder in our file structure, or just a number in our binary search tree (which we'll cover later). The value is the most important part, because otherwise why have a tree at all?

```ruby
class Node
  attr_reader :value

  def initialize(value)
    @value = value
  end
end
```

What else should our node class contain? Many times it is useful to link to the node's parent and children. This allows us to quickly move around the tree from any given node. We only kept track of children in our Queue because that was all we needed to track to make it work. The children and parent of a node can be useful, but it is not always necessary. I will leave it up to you to decide if you need it for a given application.

Another important distinction is to decide what data structure to store your children in. If node values are unique (or some part of them could be considered unique), then it might make sense to store them in a hash. This will allow for quick lookup of a given node using the value of the node as the key to the children hash. (Such as in Tries, which are covered later). If the node values are not unique, then an array makes the most sense for storage.

```ruby
class Node
  attr_reader :value
  attr_accessor :parent, :children

  def initialize(value)
    @value = value
    @parent = nil
    @children = []
  end
end
```

For most tree applications, this is all you need for the node class. What other things might be helpful? The siblings or the level for a given node might be useful for very specific tree cases. There might be other things as well. I leave it up to you to decide what to include and what to ignore.
