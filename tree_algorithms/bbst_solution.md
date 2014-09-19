# BBST Solution

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

  def balance
    return unless @head
    tree_array = in_order
    @head = nil
    add_array(tree_array)
    tree_array
  end

  def add_array(array)
    return nil if array.empty?
    return add_node(array.first) if array.length == 1
    midpoint = array.length/2
    add_node(array[midpoint])
    add_array(array[0...midpoint])
    add_array(array[(midpoint+1)..-1])
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

  def in_order
    tree_array = []
    in_order_helper(@head) do |ele|
      tree_array << ele
    end
    tree_array
  end

  def in_order_helper(node, &block)
    in_order_helper(node.left, &block) if node.left
    yield node.value
    in_order_helper(node.right, &block) if node.right
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

In order to balance the binary tree, we added several new methods:
* `balance`
* `add_array`
* `in_order`
* `in_order_helper`

```ruby
  def balance
    return unless @head
    tree_array = in_order
    @head = nil
    add_array(tree_array)
  end
```

The `balance` method calls two other new methods, `in_order` and `add_array`. In the end, this method will dismantle the binary tree and reassemble it in a balanced format. If there are no nodes in the tree, it returns before trying to balance. First, it calls `in_order`, which returns an array of the elements in sorted order. It then resets the head node to nil. Finally, it calls `add_array` with the sorted array to build out the balanced binary tree.

```ruby
  private

  def in_order
    tree_array = []
    in_order_helper(@head) do |ele|
      tree_array << ele
    end
    tree_array
  end

  def in_order_helper(node, &block)
    in_order_helper(node.left, &block) if node.left
    yield node.value
    in_order_helper(node.right, &block) if node.right
  end
```

The `in_order` method is a holder <!-- new wording for holder --> to create the sorted array of the current binary tree.

The `in_order_helper` is a recursive method to create the sorted array. It uses the in-order printing that we just went over in the previous section!

```ruby
  private

  def add_array(array)
    return nil if array.empty?
    return add_node(array.first) if array.length == 1
    midpoint = array.length/2
    add_node(array[midpoint])
    add_array(array[0...midpoint])
    add_array(array[(midpoint+1)..-1])
  end
```

The `add_array` method takes in the sorted array (it will also work with a non-sorted array, but it will create a non-balanced binary tree).

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

  def balance
    tree_array = in_order
    @head = nil
    add_array(tree_array)
  end

  def add_array(array)
    elements_to_add = [array]
    while !elements_to_add.empty?
      holder = []
      elements_to_add.each do |x|
        holder += split_and_add(x)
      end
      elements_to_add = holder
    end
  end

  private

  def split_and_add(array)
    if array.length <= 1
      add_node(array.first) if array.length == 1
      return []
    end
    midpoint = array.length/2

    add_node(array[midpoint])
    [array[0...midpoint], array[(midpoint+1)..-1]]
  end

  def in_order
    stack = []
    next_node = @head
    sol = []
    while !stack.empty? || next_node
      if next_node
        node = next_node
        next_node = node.left
        stack.push(node)
      else
        node = stack.pop
        sol << node.value
        next_node = node.right
      end
    end
    sol
  end

end
```
