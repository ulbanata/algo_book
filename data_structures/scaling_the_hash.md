# Scaling the Hash

Our current hash implementation has all of the functionality of a hash, but it isn't operating as optimally as it should be. Instead of running in O(1) time, we're still running in O(n) time! An easy solution to cut down on the run time is to increase the size of our internal array. But how often should we increase it? Just once at the beginning? We could make it 100,000 elements long at the beginning and that would take care of almost every case we could run into! While that would work, it would waste a lot of memory. The hash would create 100,000 empy arrays, just sitting there in memory, doing nothing. If you only add 3 pairs to your array, then you are using up 0.003% of the memory you allocated to your hash! There has to be a better way.

Our solution will double the hash's internal array size whenever we use up over half of the current space. Using our current hash class as an example, when we first create it, our hash has an internal array of size 4. The internal array will increase to size 8 when 3 pairs have been added to the hash. It will then increase to size 16 when 5 pairs have been added. The below graph shows the expansions:

<table>
<tr>
<th>When the inner array is size:</th>
<th>It expands when it has # of keys:</th>
</tr>
<tr>
<td>4</td>
<td>3</td>
</tr>
<tr>
<td>8</td>
<td>5</td>
</tr>
<tr>
<td>16</td>
<td>9</td>
</tr>
<tr>
<td>32</td>
<td>17</td>
</tr>
<tr>
<td>64</td>
<td>33</td>
</tr>
<tr>
<td>128</td>
<td>65</td>
</tr>
<tr>
<td>256</td>
<td>129</td>
</tr>
<tr>
<td>512</td>
<td>257</td>
</tr>
<tr>
<td>1028</td>
<td>513</td>
</tr>
</table>

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

`@key_counter` is a new instance variable that is added to the hash class. This keeps track of the number of keys that are currently in the hash. Whenever the `@key_counter` reaches a set value, then the hash will be resized to a larger value. In this case, the hash resizes whenever the number of keys is greater than half the number of internal arrays.

The method `resize` has been added to allow the hash to scale. The first thing it does is reset the `@key_counter` to 0. This is to ensure that the hash doesn't reset itself too often. Then, `holder` stores a copy of the internal array, `@arr`. The internal array is then reset and created at the new size that we passed into the method. We then go through each of the key/value pairs in the `holder` array. Each pair is re-inserted to the internal array using the `[]=` method.

## How is this efficient?

Every time we expand the internal array, we have to re-insert all of our key/value pairs! Doesn't this take a long time to run? Let's take a look at a table of the number of times a key has been inserted into the hash:

<table>
<tr>
<th>`@arr` size</th>
<th># of Keys</th>
<th># of Inserts</th>
</tr>
<tr>
<td>4</td>
<td>2</td>
<td>2</td>
</tr>
<tr>
<td>8</td>
<td>3</td>
<td>5</td>
</tr>
<tr>
<td>8</td>
<td>4</td>
<td>6</td>
</tr>
<tr>
<td>16</td>
<td>5</td>
<td>11</td>
</tr>
<tr>
<td>16</td>
<td>8</td>
<td>14</td>
</tr>
<tr>
<td>32</td>
<td>9</td>
<td>23</td>
</tr>
<tr>
<td>32</td>
<td>16</td>
<td>30</td>
</tr>
<tr>
<td>64</td>
<td>17</td>
<td>47</td>
</tr>
<tr>
<td>64</td>
<td>32</td>
<td>62</td>
</tr>
<tr>
<td>128</td>
<td>33</td>
<td>95</td>
</tr>
<tr>
<td>128</td>
<td>64</td>
<td>126</td>
</tr>
<tr>
<td>256</td>
<td>65</td>
<td>191</td>
</tr>
<tr>
<td>256</td>
<td>128</td>
<td>254</td>
</tr>
<tr>
<td>512</td>
<td>129</td>
<td>383</td>
</tr>
<tr>
<td>512</td>
<td>256</td>
<td>510</td>
</tr>
<tr>
<td>1024</td>
<td>257</td>
<td>767</td>
</tr>
<tr>
<td>1024</td>
<td>512</td>
<td>1022</td>
</tr>
</table


