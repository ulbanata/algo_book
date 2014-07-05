# Arrays

More than likely, arrays were the first data structure you were introduced to. Arrays are the workhorse of the computing world. Let's look at how they work in Ruby:

```ruby
arr = []
```

Above we created an empty array and associated it with the variable name ```arr```. We can put almost anything we want into an array.

```ruby
arr = [:hello, "test", {}, 3, 2.5, [5, 6]]
```

They can hold symbols `:hello`, strings `"test"`, hashes `{}`, integers `3`, floats `2.5`, and even other arrays `[5, 6]`. We can call any array method on our array `arr`.

Now let's look at arrays in JavaScript:

```js
arr = ["test", {}, 3, 2.5]
```

But how does it work behind the scenes? First, let's think about how memory works. We can picture our memory as a big, empty lego sheet. Whenever we store a data type or a data structure, lego blocks appear on our lego sheet to store that data. Let's put a string on our lego memory sheet. This block (Need visuals@!!!!!)

## Array Overview

Like: Lego bricks on a lego board. Adding items to the array is like adding a brick to the board. All of the bricks have to be touching each other in a line.

Uses:
* Holding a list of objects in an order

Run Times:
* Add an item to the end of the array: O(1)
* Add an item to the beginning of the array: O(n)
* Add an item somewhere in the array: O(n)
* Remove an item from the end of the array: O(1)
* Remove an item from the beginning of the array: O(n)
* Remove an item somewhere in the array: O(n)
* See if an item is in the array: O(n)
