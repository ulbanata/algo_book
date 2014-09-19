# Linked Lists
<!-- add build into ruby? Maybe also discuss other languges? -->
The linked list is a data structure that can be used to build many more detailed data structures. The basic building block is something called a **node**. The node will be talked about for several other data structures, such as trees and graphs, but in the context of the linked list, you can picture it this way:

![Node](http://i.imgur.com/k8vVPDz.png)
<!-- Maybe include a written description as well? Pros: visually impaired people, people who are not visual learners. -->
This node (represented as a <!-- color? --> rectangle) has two variables (represented as <!-- color? --> boxes inside the rectangle). The first variable (box) is the data or payload that the node stores. In this case, it is the number 3. However, it could be any datatype or object<!-- examples? -->. The second variable (box) is a pointer that points to the next node in the linked list, if one exists.

A linked list, made up of nodes, could be visualized as the structure below:

![Linked Lists](http://i.imgur.com/K2Xj8C0.jpg)

This linked list contains 5 nodes, each represented by a rectangle. The first node, the **head** node, contains the value 3 as one variable and a pointer to the second node as the second variable. The pointer points to the second node, which contains the value 7 and a pointer. These pointers continue pointing to each preceding node until we get to the last node, the **tail** node. The tail node contains the value 10 and its pointer points to null.

The linked list looks very similar to an array. Both data structures have a structure (Their position in the data structure matters and can be found). They can store any datatype or object inside themselves. So why use a linked list?

To figure out why one might be better than the other, we need to think about how linked lists are arranged in memory and then compare that to arrays. Below is an example of a linked list on a memory sheet:

![Linked List in Memory](http://i.imgur.com/pxfFEvt.png)

One thing you might notice is that, unlike arrays, the individual nodes in the linked list are not right next to each other. They exists in random locations in memory. How might this cause linked lists to have an advantage over arrays? To answer that, we need to think about the disadvantages arrays hold. We can add and remove things from the end of the array quickly, but adding or removing anything from the beginning of the array takes O(n) time to run because every following element has to be moved. To find something in the array, we need to potentially search through every element in the array to find the item, taking O(n) time.

Given the array's weaknesses, what does the linked list improve on? It improves on the adding or removing items to the beginning of (or anywhere in) the linked list! Because the individual nodes of the linked list are not packed in to each other and the pointer allows them to exist anywhere in the memory, we can add or remove any node in the linked list in O(1) time instead of O(n) time!

Below, we have an example of removing the node containing the value 12 from the linked list. The only thing that needs to change is that the pointer in the node containing the value 8 now points to the next node in the linked list.

![Removing Node in Linked List](http://i.imgur.com/oHrT30e.png)

What about searching for an item in the linked list? It will still take O(n) time because the linked list does not contain information on the location of any individual item a node contains. Hashes would be the data structure of choice to find out if something exists in the data structure in O(1) time, which will be discussed in section 4.5.

If the linked list can add items to the beginning in O(1) time, why do we use arrays? The first reason is that arrays are more memory efficient than linked lists. Pointing to the next node in the linked list does take up memory. It also makes the linked list a little more complicated than an array, and complexity should be avoided at all costs if it doesn't improve something else (Always tradeoffs!).

The other major weakness of linked lists is that you can't get to a certain node in O(1) time like you can in an array. If you remember back to arrays, the array itself knows how long it is at all times. This length knowledge as well as having the elements located next to each other in memory allows for the lookup of any element in O(1) time. For a linked list, there is no way to instantly get to the 10th, 5th or nth element in O(1) time. The linked list has to start at the first node and keep moving until it reaches the nth node. This means that to get to the nth node, the runtime is O(n). This also means that, while you can remove or add any node in a linked list in O(1) time, it could take you O(n) time to get there.

So what use is a linked list if you can't see what the nth node contains? When will it be useful? The next two data structures, stacks and queues, will dive deep into two potential uses for linked lists.

# The Code <!-- Is there going to be a description of the code? How to use it, whatever?-->

```ruby
class Node
  attr_reader :value
  attr_accessor :next

  def initialize(value)
    @value = value
    @next = nil
  end
end

class LinkedList
  def initialize
    @head = nil
    @tail = nil
  end

  def add_head_node(value)
    new_node = Node.new(value)
    unless @head
      @head = @tail = new_node
    else
      new_node.next = @head
      @head = new_node
    end
    value
  end

  def add_tail_node(value)
    new_node = Node.new(value)
    unless @head
      @head = @tail = new_node
    else
      @tail.next = new_node
      @tail = new_node
    end
    value
  end

  def remove_head_node
    return nil unless @head
    sol = @head
    @tail = nil if @tail == @head
    @head = @head.next
    sol.value
  end

  def remove_tail_node #Takes O(n) time!
    return nil unless @head
    if @head == @tail
      sol = @head.value
      @head = @tail = nil
      return sol
    end
    node = @head
    prev = nil
    while node.next
      prev = node
      node = node.next
    end
    @tail = prev
    sol = node.value
    @tail.next = nil
    sol
  end
end
```

The first thing to notice in the above code is the existence of two different classes. The first is the Node class, which, as we saw above, is the basic building block of the Linked List. Let's analyze the node:

```ruby
class Node
  attr_reader :value
  attr_accessor :next

  def initialize(value)
    @value = value
    @next = nil
  end
end
```

The node class holds the value assigned to the node with the `@value` variable and contains the pointer to the next node in the linked list with the `@next` variable. The `@next` has an attr\_accessor because we want to be able to change which node comes next at any time. The `@value` only has an attr\_reader because once it is set, we don't want to change it.

```ruby
class LinkedList
  def initialize
    @head = nil
    @tail = nil
  end
```

The LinkedList class only has two variables it needs to track, the `head` and the `tail` nodes. These are the only nodes that have to be tracked because the nodes themselves hold the rest of the structure. You can picture the linked list like a chain necklace. When you pick up the necklace, you only need to hold either end. The chains are connected to each other, so the necklace won't fall apart.

```ruby
  def add_head_node(value)
    new_node = Node.new(value)
    unless @head
      @head = @tail = new_node
    else
      new_node.next = @head
      @head = new_node
    end
    value
  end
```

To add something to the front of the list, we'll use the `add_head_node` method. This takes a value to add to the linked list and creates a new node with that value. If there is no node in the linked list (which would result in `@head` being nil), then we set the `@head` and `@tail` as the newly created node. Otherwise, we connect the new node to the old head node (using `new_node.next`) and set `@head` as the new node. Finally, we return the value.

```ruby
  def add_tail_node(value)
    new_node = Node.new(value)
    unless @head
      @head = @tail = new_node
    else
      @tail.next = new_node
      @tail = new_node
    end
    value
  end
```

To add something to the back of the list, we'll use the `add_tail_node` method. This method also takes a value and creates a node with it. Just like in the `add_head_node` method, it checks to see if there is a node in the linked list. If not, it adds the newly created node as both the `@head` and `@tail`. Otherwise, it sets the old tail's next node as the new node and sets `@tail` as the new node.

```ruby
  def remove_head_node
    return nil unless @head
    sol = @head
    @tail = nil if @tail == @head
    @head = @head.next
    sol.value
  end
```

<!--- To remove the first node, <!--- More here! --->

# Doubly Linked Lists

The linked list we looked at above is a **Singly Linked List**. Nodes only connect to the item that follows it. In a **Doubly Linked List**, each node has two pointers or connections. One connection is to the node that follows it. The other connection is to the node that precedes it.

<!-- # Doubly Image Here -->

This extra connection allows us to alleviate the O(n) runtime that we run into when removing the tail node above. Instead of having to move from the beginning until the node before the tail node, we can instead start at the tail and go in reverse. The downside to using doubly linked lists is that it does increase the amount of memory that is used.

Here is the updated linked list code:

```ruby
class Node
  attr_reader :value
  attr_accessor :next, :prev

  def initialize(value)
    @value = value
    @next = nil
    @prev = nil
  end
end

class LinkedList
  def initialize
    @head = nil
    @tail = nil
  end

  def add_head_node(value)
    new_node = Node.new(value)
    unless @head
      @head = @tail = new_node
    else
      new_node.next = @head
      @head.prev = new_node
      @head = new_node
    end
    value
  end

  def add_tail_node(value)
    new_node = Node.new(value)
    unless @head
      @head = @tail = new_node
    else
      @tail.next = new_node
      new_node.prev = @tail
      @tail = new_node
    end
    value
  end

  def remove_head_node
    return nil unless @head
    sol = @head
    @tail = nil if @tail == @head
    @head = @head.next
    sol.value
  end

  def remove_tail_node #Now takes O(1) time!
    return nil unless @head
    if @head == @tail
      sol = @head.value
      @head = @tail = nil
      return sol
    end
    sol = @tail.value
    @tail = @tail.prev
    @tail.next = nil
    sol
  end
end
```

So let's review Linked Lists:

* O(1) to add or remove a node (Faster than an array for any node added before the beginning)
* O(n) to get to the nth node (Slower than an array)
* O(n) to see if something is in the linked list (Same as an array)
* Structured- The node exists in a location (Same as an array) <!-- Go into this one more in the section! -->
