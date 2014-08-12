# Stacks

The stack data structure is a useful data structure with many different uses. Stacks can be pictured as a stack of plates. As you add plates to the stack, you always add them to the top, not the bottom. Whenever you take a plate away, you grab it from the top of the stack. This is a Last-in, First-out data structure, where the last item that was added to the stack is the first item that is removed.

You can use an array to implement the functionality of a stack. Let's take a look at what that would look like.

We start with a stack with one element, 36. 54 is being added to the stack.

![Stack](http://i.imgur.com/q8HLdwo.png)

Now our stack has two elements, 36 and 54. 36 is on the bottom of the stack and 54 is on the top. 15 is being added to the stack.

![Stack](http://i.imgur.com/2nQZxMa.png)

Our stack has three elements, 36, 54 and 15. 36 is on the bottom of the stack and 15 is on the top. We add 47 to the stack.

![Stack](http://i.imgur.com/gPzoZlm.png)

Time to start taking items away! Because 47 was the last element added to the stack, it is the first element removed. (Last in, First out)

![Stack](http://i.imgur.com/4yV9GCb.png)

We can repeat this process with the last three elements as well.

![Stack](http://i.imgur.com/mqtbQ5T.png)
![Stack](http://i.imgur.com/l80QyAl.png)
![Stack](http://i.imgur.com/AVWZSoD.png)

Take a minute to think about why an array can work for the stack data structure. The two methods that are being used on the stack are `push` and `pop`. They are doing the same thing for a stack as they would for an array: adding an element to the end or removing the element at the end. Now, if we think about the Big O of those two methods, it seems that an array is already really fast, `O(1)` for both `push` and `pop`! In the case of a stack, using an array to build out your stack makes perfect sense.

However, a word of warning. If you want your stack to only be able to take and add items to the top of the stack, using an array could cause issues. Someone that comes behind you might use `.shift` or something similar, nullifying the purpose of the stack. If this is the case, a custom stack class is your best bet. Below is the code for a basic stack. <!-- more explaination woudl be nice. Discussion of basing it off of the ruby Array class, etc. -->

```ruby
class Stack
  def initialize
    @arr = []
  end

  def push(element)
    @arr.push(element)
    element
  end

  def pop
    @arr.pop
  end

  def peek
    @arr.last
  end
end
```

## Stack Overview

Like: A stack of plates. You add new plates to the top of the stack and remove plates from the top as well. Last In-First Out (LIFO) Data Structure.

Uses: Undo- Keeps track of last command ran in order to undo it as needed.

Run Times:
* Adding an item: O(1)
* Removing an item: O(1)
* Viewing the next item to be removed: O(1)

Best built using an array. <!-- How do you know this? -->
