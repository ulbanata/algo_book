# BST Solution

## Recursive Solution

```ruby
class Node
  attr_reader :value
  attr_accessor :left, :right

  def initialize(value)
    @value = value
    @left = nil
    @right = nil
  end
end

class Tree

  def initialize
    @head = nil
  end

  def add_node(value)
    return @head = Node.new(value) unless @head
    add_helper(value, @head)
  end

  def search?(value)
    search_helper?(value, @head)
  end

  private

  def search_helper?(value, node)
    if value == node.value
      return true
    elsif value < node.value && node.left
      search_helper?(value, node.left)
    elsif value > node.value && node.right
      search_helper?(value, node.right)
    else
      return false
    end
  end

  def add_helper(value, node)
    if node.value == value
      return node
    elsif value < node.value
      if node.left
        add_helper(value, node.left)
      else
        node.left = Node.new(value)
      end
    else
      if node.right
        add_helper(value, node.right)
      else
        node.right = Node.new(value)
      end
    end
  end

end
```

Once again, we'll start with the node class:

```ruby
class Node
  attr_reader :value
  attr_accessor :left, :right

  def initialize(value)
    @value = value
    @left = nil
    @right = nil
  end
end
```

Being a binary tree, we need to keep track of the value of the node and its left and right children. The parent of a given node isn't important in this application. We are also assuming that once a node is added to the tree, we won't need to change its value, so we give the value an att_reader.

```ruby
class Tree

  def initialize
    @head = nil
  end
```

The tree class only needs to keep track of the head node. It is set to nil initially.

```ruby
  def add_node(value)
    return @head = Node.new(value) unless @head
    add_helper(value, @head)
  end
```

Adding a node to the tree first checks to see if there is a node in the tree. If there is not, it creates the new node and sets it as the head. Otherwise, it calls the `add_helper` method, which is our recursive method to add the node.

```ruby
  private

  def add_helper(value, node)
    if node.value == value
      return node
    elsif value < node.value
      if node.left
        add_helper(value, node.left)
      else
        node.left = Node.new(value)
      end
    else
      if node.right
        add_helper(value, node.right)
      else
        node.right = Node.new(value)
      end
    end
  end
```

The `add_helper` method takes in a value and a node. The node that is passed in is the current position in the tree that the method is trying to add the node. There are three possible outcomes: the value can be equal to the current node's value, the value can be less than the current node's value, or the value can be greater than the current node's value.

The first `if` statement checks to see if the current node's value is equal to the value we are trying to add to the tree. If so, it exits the method and returns the node. This method is one of our base cases.

The `elsif` statement checks to see if the value we are passing in is less than the current node's value. If this is true, an inner `if` statement determines if the current node has a left child or not. If the current node has a left child, then the `add_helper` method is called again. It is passed the value and the left child of the current node. This is a recursive case of the `add_helper` method. If the current node does not have left child, a new node is created with the value and is set as the current node's child. This is a base case of the `add_helper` method.

The `else` case occurs if the the value we are passing in is greater than the current node's value. This portion follows the exact same process as the `elsif` statement, except it uses the current node's right child.

```ruby
  def search?(value)
    search_helper?(value, @head)
  end
```

The `search?` method only makes a call to the `search_helper?` recursive method, passing in the value to be searched for and the head node, which is the starting point.

```ruby
  private

  def search_helper?(value, node)
    if value == node.value
      return true
    elsif value < node.value && node.left
      search_helper?(value, node.left)
    elsif value > node.value && node.right
      search_helper?(value, node.right)
    else
      return false
    end
  end
```

The `search_helper?` method is a tree traversal method that is searching for a particular value. The two inputs, the `value` and the `node`, correspond to the value we are searching for and the current node we are searching, respectively. The entire method turns into a large if statement. If the current node's value is equal to the value we are searching for, then we return true. This is a base case of the `search_helper?` method.

Otherwise, the method has to search the two children of the current node. The first `elsif` results in a recursive call for the left child of the current node if the value that is being searched for is less than the current node's value and the current node has a left child. The second `elsif` results in a recursive call for the right child of the current node if the value that is being searched for is greater than the current nodes' value and the current node has a right child.

If none of the `if` statements' are satisified, then the value being searched for is not in the binary tree and the method exits by returning false. This is a base case.

```ruby

```

## Iterative Solution

```ruby
class Node
  attr_reader :value
  attr_accessor :left, :right

  def initialize(value)
    @value = value
    @left = nil
    @right = nil
  end
end

class Tree
  attr_reader :head

  def initialize
    @head = nil
  end

  def add_node(value)
    return @head = Node.new(value) unless @head
    node = @head
    while node
      if value == node.value
        return node
      elsif value < node.value
        if node.left
          node = node.left
        else
          node.left = Node.new(value)
          node = nil
        end
      else
        if node.right
          node = node.right
        else
          node.right = Node.new(value)
          node = nil
        end
      end
    end
  end

  def search?(value)
    node = @head
    while node
      if value == node.value
        return true
      elsif value < node.value && node.left
        node = node.left
      elsif value > node.value && node.right
        node = node.right
      else
        return false
      end
    end
  end

end
```
