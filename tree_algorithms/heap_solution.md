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

  def get_children(parent)
    [parent * 2 + 1, parent * 2 + 2]
  end

  def get_parent(child)
    (child - 1)/2
  end

  def swap(index1, index2)
    @arr[index1], @arr[index2] = @arr[index2], @arr[index1]
  end

  def bubble_up(child)
    return if child == 0
    parent = get_parent(child)
    if @arr[child] > @arr[parent]
      swap(child, parent)
      bubble_up(parent)
    end
  end

  def bubble_down(parent)
    child1, child2 = get_children(parent)
    if @arr[child2]
      if @arr[parent] < @arr[child1] && @arr[child1] >= @arr[child2]
        swap(parent, child1)
        bubble_down(child1)
      elsif @arr[parent] < @arr[child2] && @arr[child2] >= @arr[child1]
        swap(parent, child2)
        bubble_down(child2)
      end
    elsif @arr[child1] && @arr[parent] < @arr[child1]
      swap(parent, child1)
      bubble_down(child1)
    end
  end
end
```

The solution for the Heap, while complicated, is still simpler than the Priority Queue. Time to break it down.

```ruby
class Heap
  def initialize
    @arr = []
  end
```

The Heap class has an internal array that stores all of the values of the heap.

```ruby
def push(value)
    @arr.push(value)
    bubble_up(@arr.length - 1)
    value
  end
```

The `push` method takes in a value and adds it to the end of the internal array, `@arr`. After adding the value to the array, it then moves the newly added value to its correct spot in the array using the `bubble_up` method. Finally, it returns the value that was inputted.

```ruby
  def pop
    return nil if @arr.length == 0
    return @arr.shift if @arr.length == 1
    sol = @arr.first
    @arr[0] = @arr.pop
    bubble_down(0)
    sol
  end
```

The `pop` method is more complicated than the `push` method. The first line returns nil if there is no value in the heap. The second line checks to see if there is only one item in the heap. If this is true, it removes the value from the internal array and returns it.

Lines 3-5 allow for the removal of values from heaps with two or more values. `sol = @arr.first` saves the value that will be returned at the end of the method. `@arr[0] = @arr.pop` removes the last value from the internal array and saves it as the first item. The `bubble_down` method on line 6 is called to reorder the internal array into the correct heap format. Finally, the value that was saved in line 3 is returned in line 6.

```ruby
  def peek
    @arr.first
  end
```

The `peek` method is self-explanatory. It looks at the item on top of the heap and returns it, without modifying the heap.

The first 3 `private` methods are helper methods designed to ***dry*** up our code.

```ruby
  def get_children(parent)
    [parent * 2 + 1, parent * 2 + 2]
  end
```

The `get_children` method takes the index of a parent in the internal array and returns the indices that would contain the children in the internal array.

```ruby
  def get_parent(child)
    (child - 1)/2
  end
```

The `get_parent` method is the opposite of the `get_children` method. It takes in the index of a child element and returns the index at which the parent element will be located.

```ruby
  def swap(index1, index2)
    @arr[index1], @arr[index2] = @arr[index2], @arr[index1]
  end
```

The `swap` method swaps the location of two elements in the internal array. Pass in the two indices of the elements that should be swapped to make it work.

```ruby
  def bubble_up(child)
    return if child == 0
    parent = get_parent(child)
    if @arr[child] > @arr[parent]
      swap(child, parent)
      bubble_up(parent)
    end
  end
```

The `bubble_up` method is a recursive method that takes in the index of the child element. The first line checks if the child index is 0 (if the child is the first element in the internal array). If this is true, then the `bubble_up` method is complete and the return statement exits out of the method. This is a base case.

Line 2 grabs the location of the parent for the given child location. Line 3 is a conditional statement that checks to see if the given child is larger than the parent. If this is true, line 4 has the child and parent swap locations (just like the bubble up for the priority queue). After the child and parent have been swapped, the recursive call is made on line 5. If the conditional on line 3 is false, then the method will exit.

For this class, we won't need an iterative version of the `bubble_up method`. Why? This can be answered by determining the Big O of the `bubble_up` method! In order to bubble a value from the end of the array to the front will take `O(log(n))` operations to complete. For a heap, the number of recursive method calls that are made can never be higher than ***log(n)***. If we have 100 trillion items in our heap, it will only need to make 37 method calls to bubble up the newly added value.

```ruby
  def bubble_down(parent)
    child1, child2 = get_children(parent)
    if @arr[child2]
      if @arr[parent] < @arr[child1] && @arr[child1] >= @arr[child2]
        swap(parent, child1)
        bubble_down(child1)
      elsif @arr[parent] < @arr[child2] && @arr[child2] >= @arr[child1]
        swap(parent, child2)
        bubble_down(child2)
      end
    elsif @arr[child1] && @arr[parent] < @arr[child1]
      swap(parent, child1)
      bubble_down(child1)
    end
  end
```

The `bubble_down` method also takes an index as its parameter.
