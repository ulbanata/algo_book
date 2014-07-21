# Sets

The idea of a set comes to us from mathematics. A set is a collection of distinct objects. We can consider an array as a collection of objects.

```
array = [1,2,3,4,4,4,5,5,7]
```

A set contains **distinct** objects, meaning that there will be no repeating objects within the set. If we converted our array above to a set, it would look something like this:

```
set = {1,2,3,4,5,7}
```

The set now contains only one copy of each object. Whenever you add an object to a set, it will first check to see if the object already exists in the set. If so, then it doesn't need to do anything. Otherwise, it will add the object.

There is a built-in Set class in Ruby, but we will build out our own version. Let's start by determining what data structure to use internally. We have several to choose from now! We could use an array, a linked list or a hash. What would make the most sense?

We are only storing individual objects, so an array might make sense. We'll build out a **set** class using an array as our internal data structure. We will need methods to add and remove objects to the set. We also need a method to see if an object exists in a set.

```ruby
class Set
  def initialize
    @arr = []
  end

  def add(obj)
    @arr.push(obj) unless include?(obj)
  end

  def remove(obj)
    @arr.remove(obj)
  end

  def include?(obj)
    @arr.include?(obj)
  end
end
```

That was simple enough! We have a set class that can add and remove individual objects and also check to see if something exists in the set. But how long does it take to run these methods? We know that the runtime of `.include?` is O(n), so adding an object will take O(n) time because we call the `.include?` method before pushing into our internal array. The `.remove` method takes O(n) time to run, because it is running through every element in the array! That means that all 3 of our methods takes O(n) time. That's not very efficient. We can do better, but what data structure should we use? A hash or a linked list?

The answer might sound counter-intuitive at first, but it makes more sense to use a hash as our internal data strucuture! The hash contains key-value pairs and has O(1) lookup. We're going to use the hash to store the object being stored in our sort as the key and the value of every object stored will be the value. Let's take a look at what the code would be:

```ruby
class Set
  def initialize
    @hash = Hash.new(false)
  end

  def add(obj)
    @hash[obj] = true
  end

  def remove(obj)
    @hash.delete(obj)
  end

  def include?(obj)
    @hash[obj]
  end
end
```

Our set now runs in O(1) time to add, remove and see if an item is in the set! We initialized our set with an empty hash and set the default value to false. This means that any object that is not included in the hash will return false when the `.include?` method is called. Adding an object to the set is as simple as using `@hash[obj] = true`. Now, when we use `.include?` on the set for an object that is added to the set, it will return true. The `.remove` method uses the built-in `.delete` method for hashes to remove an object from the set.
