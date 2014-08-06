# Priority Queue Solution
```ruby
class Node
  attr_accessor :l_child, :r_child, :l_count, :r_count, :parent, :value

  def initialize(value)
    @value = value
    @l_child = nil
    @l_count = 0
    @r_child = nil
    @r_count = 0
    @parent = nil
  end
end

class PriQueue
  attr_reader :head

  def initialize
    @nodes = {}
    @head = nil
  end

  def push(value)
    unless @head
      @head = Node.new(value)
    else
      node = add_node(value, @head)
      bubble_up(node)
    end
    value
  end

  def pop
    return nil unless @head
    res = @head.value
    if @head.l_count == 0
      @head = nil
    else
      remove_node(@head)
      bubble_down(@head)
    end
    res
  end

  def print
    print_helper(@head)
  end

  def print_helper(node)
    puts node.value
    print_helper(node.l_child) if node.l_child
    print_helper(node.r_child) if node.r_child
  end

  private

  def bubble_down(node)
    if node.l_child && node.r_child
      if node.value < node.l_child.value && node.l_child.value >= node.r_child.value
        swap(node.l_child, node)
        bubble_down(node.l_child)
      elsif node.value < node.r_child.value && node.r_child.value >= node.l_child.value
        swap(node.r_child, node)
        bubble_down(node.r_child)
      end
    elsif node.l_child
      if node.value < node.l_child.value
        swap(node.l_child, node)
        bubble_down(node.l_child)
      end
    elsif node.r_child
      if node.value < node.r_child.value
        swap(node.r_child, node)
        bubble_down(node.r_child)
      end
    end
  end

  def remove_node(node)
    if node.r_count >= node.l_count
      if node.r_count == 1
        @head.value = node.r_child.value
        node.r_child = nil
        node.r_count -= 1
      else
        node.r_count -= 1
        remove_node(node.r_child)
      end
    else
      if node.l_count == 1
        @head.value = node.l_child.value
        node.l_child = nil
        node.l_count -= 1
      else
        node.l_count -= 1
        remove_node(node.l_child)
      end
    end
  end

  def add_node(value, node)
    if !node.l_child
      new_node = Node.new(value)
      node.l_child = new_node
      new_node.parent = node
      node.l_count += 1
      new_node
    elsif !node.r_child
      new_node = Node.new(value)
      node.r_child = new_node
      new_node.parent = node
      node.r_count += 1
      new_node
    elsif node.l_count > node.r_count
      node.r_count += 1
      add_node(value, node.r_child)
    else
      node.l_count += 1
      add_node(value, node.l_child)
    end
  end

  def bubble_up(node)
    if node.parent && node.value > node.parent.value
      swap(node, node.parent)
      bubble_up(node.parent)
    end
  end

  def swap(child_node, parent_node)
    child_node.value, parent_node.value = parent_node.value, child_node.value
  end
end
```
