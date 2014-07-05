# Queues

Queues are like lines at an amusement park. As people get in line, they get in the back of it. Whenever someone gets to get on the ride, they leave the line from the front of it. The queue is an example of First-in, First-out data structure, where the first item that was added to the queue is the first item that is removed.

While queues can be implemented using arrays, it is not the most efficient way. Let's look at what's happening with a queue to understand where the inefficiencies lie.

We'll start with a queue that has 36 as the first element. 54 is being added to the queue.

![Queue](http://i.imgur.com/MWq6u6b.png)

The queue now has two elements, 36 and 54. 36 is the first element. 15 is being added to the queue, and will be added to the end.

![Queue](http://i.imgur.com/G2eeS0i.png)

The queue now has three elements, 36, 54 and 15. 36 is the first element and 15 is the last element. 47 is being added to the queue and will be added to the end.

![Queue](http://i.imgur.com/VxFnjuK.png)

Our queue now has 4 elements, 36, 54, 15, and 47. 36 is the at the beginning of our queue and 47 is at the end. When we remove an item with queue.shift, we remove 36 because it is at the beginning. This is the opposite of removing items from the stack.

![Queue](http://i.imgur.com/kxo1sdH.png)

The removal process can be repeated to remove the remaining elements from our queue.

![Queue](http://i.imgur.com/Y5jO22Q.png)
![Queue](http://i.imgur.com/pzlNM95.png)
![Queue](http://i.imgur.com/al7TAfr.png)

Now that we've gone through how the queue works, let's take a minute to determine why we wouldn't want to use an array to store our queue elements. It comes down to the commands that are being used. We want to be able to both add and remove items in `O(1)` time, but can we do that using an array in our queue? We already know that the `array.push` method takes `O(1)` time. What about `array.shift`? If you remember back to the array section, `array.shift` runs in `O(n)` time! The larger our queue grows, the slower it will get if we use arrays to store our elements. Is all lost? Not necessarily! We're going to build our own data structure from scratch!  Let's take a look at the code we can use to build it.

```ruby
class Node
  attr_accessor :child
  attr_reader :value
  def initialize(value)
    @value = value
    @child = nil
  end
end

class Queue
  def initialize()
    @start = nil
    @end = nil
  end

  def push(value)
    node = Node.new(value)
    if @end
      @end.child = node
      @end = node
    else
      @start = node
      @end = node
    end
    value
  end

  def shift
    if @start
      value = @start.value
      @end = nil if @start == @end
      @start = @start.child
    else
      return nil
    end
    value
  end

  def peek
    @start ? @start.value : nil
  end

end
```

There's a lot going on here! Time to break it down.

```ruby
class Node
  attr_accessor :child
  attr_reader :value
  def initialize(value)
    @value = value
    @child = nil
  end
end
```

The node class is the basic building block of our queue. It only has two instance variables, a `value` and a `child`. The `value` holds whatever we are storing in the queue, such as a number, an instance of a class, or a hash. The `child` is the connector that attaches one node to another. Because we only have the `child` variable, we can only from the front to the end of the queue. However, there isn't a case for going back the other direction, so a `parent` variable is not needed. The node has to have a `value` to be initialized, but the `child` can be set at any time via the `attr_accessor`. The `value` only has an `attr_reader`, so it cannot be changed by anything outside of the node class. This is to protect the data in the queue.

```ruby
class Queue
  def initialize()
    @start = nil
    @end = nil
  end
```

Here is the beginnings of our queue class. We only have two instance variables, the `start` and the `end` which point to the beginning and end of our queue, respectively. That is the only thing we need to track within our queue. We need to be able to remove object from the front, using the `start` variable, and we need to add items to the end, using the `end` variable.

```ruby
  def push(value)
    node = Node.new(value)
    if @end
      @end.child = node
      @end = node
    else
      @start = node
      @end = node
    end
    value
  end
```

To add items to our queue, we will build our own push method. It takes a `value` as a parameter and uses the value to create a new node. The `end` instance variable is used to see how to add the node to the queue. If there is a node in the queue, then `end` will equal `true`. In this case, the current end node has its child set to the node being added, and the `end` variable is set to the new node.

If there are no nodes in the queue, then the if-else statement will run the code in the else block. It will set both the `start` and the `end` variables to the node, because it is now the only node in the queue.

Finally, the push method returns the value.

```ruby
  def shift
    if @start
      value = @start.value
      @end = nil if @start == @end
      @start = @start.child
    else
      return nil
    end
    value
  end
```

A shift method is created to remove individual items from the queue. The flow of the shift method follows the basic flow of the push method. If there is a `start` node, then you save the value to a `value` variable. Then, you replace the `start` node with its child. In order to make sure that you update the `end` variable if you are removing the last item in the queue (in the case above, it was when we used queue.shift on 47). This sets the `end` to nil, because there are no more elements in our queue. Finally, the method returns the `value`.

If `start` is nil (there are no elements in the queue), then it returns `nil`.

```ruby
  def peek
    @start ? @start.value : nil
  end
  ```

  The peek method

## Queue Overview

Like: A line waiting to get on a ride. The first person in line is the one that gets to get on the ride first. New people that join the line join at the end of the line. Example of a First In, First Out (FIFO) Data Structure.

Uses:
* Commands to be ran on a server

Run Times:
* Adding an item: O(1)
* Removing an item: O(1)
* Viewing the next item to be removed: O(1)

Best built using a linked list.
