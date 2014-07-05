# Hash Collisions Part II

Our hash is coming along nicely. We can store key/value pairs and we only get a value back if our key/value pair are already in the hash. But our key/value pairs can still overwrite each other. To solve this, we can store multiple key/value pairs per index in our internal array. This will give us the flexibility to add any number of pairs to our hash. The code would look something like this:

```ruby
class MyHash

  def initialize
    @arr = Array.new(4) {[]}
  end

  def []=(key,value)
    index = find_index(key)
    @arr[index].each do |pair|
        return pair[-1] = value if pair.first == key
    end
    @arr[index] << [key, value]
  end

  def [](key)
    index = find_index(key)
    @arr[index].each do |pair|
        return pair.last if pair.first == key
    end
    nil
  end

  def find_index(key)
    key.hash % @arr.length
  end

end
```

It took a little more code to fix the issue overwriting key/value pairs than it did to not return the incorrect value for a given key. Three methods had to be edited. The first was the `initialize` method. Instead of creating an empty 4 element array with `@arr = Array.new(4)`, we are creating a 4 element array with empty arrays within each element with `@arr = Array.new(4) {[]}`. We can then add multiple key/value pairs to each index in our `@arr` array.

The `[]=(key,value)` method was also changed. To go through all of the pairs for a given index in the `@arr[index].each do |pair|` array, a `.each` loop was used. Within this loop, we check to see each pair's key is the same as the key we passed in, `... if pair.first == key`. If so, then we edit the value associated with the key and exit the method, `return pair[-1] = value ...`. If the key hasn't been used yet, then the key/value pair is added to the array with `@arr[index] << [key, value]`.

Finally, `[](key)` was also changed. It is now close to a mirror of the `[]=(key,value)` method. The `return nil unless @arr[index]` line was removed because that error can no longer occur with the new code. In its place, we have a loop that is running through all of the pairs for the given index, `@arr[index].each do |pair|`. Within this loop, we return a value if the given key matches the saved key, `return pair.last if pair.first == key`. If nothing matches, the `nil` at the end of the method returns the nil value.

The new MyHash class can now add key/value pairs and return values for a given key without overwriting any pair. We have a fully working hash! Though is this an improvement over an array? If we add 20,000 key/value pairs to our hash, then we still have to, on average, search through 5,000 pairs. Instead of running in O(n) time, we're running in O(n/4) time. That's an improvement, but nothing like the O(1) time we were expecting and it is still comparable to O(n). An easy solution would be to increase our internal array's size. It's time to scale up our hash!
