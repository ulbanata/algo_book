# Building out a Hash

Figure it out yet? If not, here's a couple hints: Think about how arrays work. If you want to find something in an array, you potentially have to look at every element in the array. This results in `O(n)` time. But if you know where something should be located by knowing the index, then looking up an element is just `O(1)` time! How can we use the `.hash` method in conjunction with looking an item up by the index?

If you're thinking that we can use the `.hash` as our index, you're almost correct! The main problem with using the `.hash` as the index is that our array is going to be huge! A 64 bit number can be any number from 0 to 18,446,744,073,709,551,615. That's a big array! And if you're only storing 4 things in your hash, that's a lot of memory to take up to store 4 items. Another thing you might have noticed is that the `.hash` method can also return negative numbers. What's a good fix for this?

The modulo (%)! If we know how big our internal array is in our hash, we can use the modulo operator on our `.hash` to find the index we should insert our item. Now that we have the basics down, let's get to some code.

```ruby
class MyHash

  def initialize
    @arr = Array.new(4)
  end

  def []=(key,value)
  end

  def [](key)
  end

  def find_index(key)
    key.hash % @arr.length
  end

end
```

Now that we have our `find_index` method complete, let's get to where we can add to our hash.

```ruby
class MyHash

  def initialize
    @arr = Array.new(4)
  end

  def []=(key,value)
    index = find_index(key)
    @arr[index] = value
  end

  def [](key)
  end

  def find_index(key)
    key.hash % @arr.length
  end

end
```

To add items, we first grab the index using our `find_index` method and passing it our key, then we save our value in our internal array at the index.

Now let's add functionality to grab a value given a key:

```ruby
class MyHash

  def initialize
    @arr = Array.new(4)
  end

  def []=(key,value)
    index = find_index(key)
    @arr[index] = value
  end

  def [](key)
    index = find_index(key)
    @arr[index]
  end

  def find_index(key)
    key.hash % @arr.length
  end

end
```

The code to return a value given a key is almost the same as adding a value to the hash. The only difference is instead of saving the value, we're just locating it using the index. This results in `O(1)` time to insert and grab a value! But we're not quite done...

Do you see where the above code could have problems? Take a couple minutes to think about what issues our current implementation might run into.
