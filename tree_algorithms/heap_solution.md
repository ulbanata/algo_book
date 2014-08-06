# Heap Solution

```ruby
class Heap
  def initialize
    @arr = []
  end

  def push(value)
    @arr.push(value)
    bubble_up(@arr.length - 1)
    value
  end

  def pop
    return nil if @arr.length == 0
    return @arr.shift if @arr.length == 1
    sol = @arr.first
    @arr[0] = @arr.pop
    bubble_down(0)
    sol
  end

  def peek
    @arr.first
  end

  private

  def bubble_up(current)
    return if current == 0
    parent = get_parent(current)
    if @arr[current] > @arr[parent]
      swap(current, parent)
      bubble_up(parent)
    end
  end

  def get_children(parent)
    [parent * 2 + 1, parent * 2 + 2]
  end

  def get_parent(child)
    (child - 1)/2
  end

  def swap(ele1, ele2)
    @arr[ele1], @arr[ele2] = @arr[ele2], @arr[ele1]
  end

  def continue_bubbling?(parent, child1, child2)
    if @arr[parent] < @arr[child1] || @arr[parent] < @arr[child2]
      true
    else
      false
    end
  end

  def bubble_down(current)
    children = get_children(current)
    if @arr[children[1]]
      if @arr[current] < @arr[children[0]] && @arr[children[0]] >= @arr[children[1]]
        swap(current, children[0])
        bubble_down(children[0])
      elsif @arr[current] < @arr[children[1]] && @arr[children[1]] >= @arr[children[0]]
        swap(current, children[1])
        bubble_down(children[1])
      end
    elsif @arr[children[0]] && @arr[current] < @arr[children[0]]
      swap(current, children[0])
      bubble_down(children[0])
    end
  end
end
```
