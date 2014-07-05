# Hash Collisions

The first problem that we should solve is that our key/value pairs can overwrite each other! How can this happen? Our keys can have the same number if our hashes have the same remainder from the modulo method. When this occurs, the key/value pair that is being added to the hash will overwrite the current key/value pair. Let's look at an example in irb:

```
:001 > load 'hash.rb'
 => true
:002 > hash = MyHash.new
 => #<MyHash:0x0000010110a728 @arr=[nil, nil, nil, nil]>
:003 > hash[3] = 3
 => 3
:004 > hash
 => #<MyHash:0x0000010110a728 @arr=[nil, nil, 3, nil]>
:005 > hash[5] = 5
 => 5
:006 > hash
 => #<MyHash:0x0000010110a728 @arr=[nil, nil, 5, nil]>
:007 > hash[3]
 => 5
```

Line 1 we're loading up our hash.rb file. Line 2 is creating an instance of the MyHash class and saving it to the variable hash. On line 3 we add the value **3** to our hash under the key **3**. Line 4 returns to us the hash object and we can see that 3 is being stored in our internal array. Line 5 adds a value **5** to the hash under the key **5**. However, on line 6, when we look at our hash object, we notice that the internal array doesn't hold our 3 anymore! It only has `@arr=[nil, nil, 5, nil]`. Putting in the key/value pair `5 => 5` overwrote the key/value pair `3 => 3`! On line 7, we can see that when we try to get the value out for key **3**, it returns 5 instead. That's a big problem! Overwriting our key/value pair is one thing, but returning a value that we didn't put in can't be tolerated. We need to make sure that we don't give back a wrong value.

We'll need to add some code to make sure we don't return a wrong value for a given key. One way we can do this is by storing the key with the value in our internal array. Then, when we want to retrieve a value, we return the value only when the key that is passed in matches the key that we have saved.

```ruby
class MyHash

  def initialize
    @arr = Array.new(4)
  end

  def []=(key,value)
    index = find_index(key)
    @arr[index] = [key, value]
  end

  def [](key)
    index = find_index(key)
    return nil unless @arr[index]
    @arr[index].last if @arr[index].first == key
  end

  def find_index(key)
    key.hash % @arr.length
  end

end
```

Two methods were changed to make sure our hash won't return the wrong value. The first was our `[]=(key,value)` method. We changed the `@arr[index] = value` to `@arr[index] = [key, value]`. Now we're storing the key/value pair in an array instead of just the value.

Storing the key/value pair comes in handy in our `[](key)` method. Two lines were changed in this method. The first, `return nil unless @arr[index]`, is brand new. This new line will return nil if there isn't anything stored in our array. It avoids a `NoMethodError: undefined method 'first' for nil:NilClass` error that could be caused by the second line if a key/value pair hasn't been added to that specific index yet. (Try it out yourself, don't add in the line to our method, then run `hash[2]`. It should return nil instead of causing an error.)

The second line changed, `@arr[index].last if @arr[index].first == key` was previously `@arr[index]`. This line now checks to see if the key associated with a key/value pair, `@arr[index].first`, is the same key that was passed in, `key`. If this is true, then it returns the value, `@arr[index].last`.

That takes care of our wrong value problem, but what about overwriting existing key/value pairs? What can we do about that?
