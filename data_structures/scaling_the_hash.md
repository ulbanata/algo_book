# Scaling the Hash

Our current hash implementation has all of the functionality of a hash, but it isn't operating as optimally as it should be. Instead of running in O(1) time, we're still running in O(n) time! An easy solution to cut down on the run time is to increase the size of our internal array. But how often should we increase it? Just once at the beginning? We could make it 100,000 elements long at the beginning and that would take care of almost every case we could run into! While that would work, it would waste a lot of memory. The hash would create 100,000 empy arrays, just sitting there in memory, doing nothing. If you only add 3 pairs to your array, then you are using up 0.003% of the memory you allocated to your hash! There has to be a better way.

Our solution will double the hash's internal array size whenever we use up over half of the current space. Using our current hash class as an example, when we first create it, our hash has an internal array of size 4. The internal array will increase to size 8 when 3 pairs have been added to the hash. It will then increase to size 16 when 5 pairs have been added. By

```ruby
class MyHash

  def initialize
    @arr = Array.new(4) {[]}
    @key_counter = 0
  end

  def []=(key,value)
    @key_counter += 1
    resize(@key_counter * 2) if @key_counter > @arr.length/2
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

  def resize(new_size)
    @key_counter = 0
    holder = @arr
    @arr = Array.new(new_size) {[]}
    holder.each do |index_arrays|
      index_arrays.each do |pairs|
        self.[]=(pairs.first, pairs.last)
      end
    end
  end
end
```
