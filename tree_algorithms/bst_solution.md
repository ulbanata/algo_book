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
  attr_reader :head

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
    tree_array = in_order
    @head = nil
    add_array(tree_array)
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
    @tree_array = []
    in_order_helper(@head)
    @tree_array
  end

  def in_order_helper(node)
    in_order_helper(node.left) if node.left
    @tree_array << node.value
    in_order_helper(node.right) if node.right
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
