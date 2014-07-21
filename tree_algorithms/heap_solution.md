# Heap Solution

```ruby
class Heap
  def initialize
    @arr = []
  end

  def push(ele)

  end

  def shift
    sol = arr.first
    arr[0] = arr.pop
    bubble_down
  end

  def peek
    arr.first
  end

  private

  def get_children(parent)
    [parent * 2 + 1, parent * 2 + 2]
  end

  def get_parent(child)
    (child - 1)/2
  end

  def continue_bubbling?(parent, child1, child2)
    if parent > child1 || parent > child2
      true
    else
      false
    end
  end

  def bubble_down
    current = 0
    children = get_children(current)
    while continue_bubbling?(current, children[0], children[1])

    end
  end
end
```
