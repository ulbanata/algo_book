# Insertion Sort Solution

```ruby
def insertion_sort(arr)
  array = arr.dup
  (1...array.length).each do |i|
    j = i
    while j > 0
      if array[j] < array[j-1]
        holder = array[j]
        array[j] = array[j-1]
        array[j-1] = holder
        j -= 1
      else
        j = 0
      end
    end
  end
  array
end
```

```ruby
def insertion_sort(arr)
  array = arr.dup
```

The `insertion_sort` method takes in the array to be sorted. The first line, `array = arr.dup`, makes a copy of the array being sorted. This is required due to the fact that changing the values of an array given the indices will edit the original array. To see what happens without this line, copy the text and comment it out. Save an unsorted array to a variable and then use `insertion_sort` on your array. `insertion_sort` will return a sorted array, but if you check the value of your variable, it will be sorted as well!

```ruby
def insertion_sort(arr)
  array = arr.dup
  (1...array.length).each do |i|
  j = i
```

To complete insertion_sort, `(1...array.length).each do |i|` iterates through each index in the array. This index is used to determine where to start the swapping process from, which can be seen in the line `j = i`.

```ruby
def insertion_sort(arr)
  array = arr.dup
  (1...array.length).each do |i|
    j = i
    while j > 0
      if array[j] < array[j-1]
        holder = array[j]
        array[j] = array[j-1]
        array[j-1] = holder
        j -= 1
      else
        j = 0
      end
    end
```

Another loop is used for the actual swapping process (notice the loop-within-a-loop, the tell-tale sign of an O(n<sup>2</sup>) method!). `while j > 0`, the swapping method is going to compare the element at j with it's preceding element. This can be seen with the `if array[j] < array[j-1]` line. If this line returns true, the elements are swapped using a holder to aid in the swapping and j is decremented by one. Otherwise, j is set to 0, which causes the while loop to exit.

```ruby
def insertion_sort(arr)
  array = arr.dup
  (1...array.length).each do |i|
    j = i
    while j > 0
      if array[j] < array[j-1]
        holder = array[j]
        array[j] = array[j-1]
        array[j-1] = holder
        j -= 1
      else
        j = 0
      end
    end
  end
  array
end
```

Once the swapping has been performed for every index in the array, the method ends by returning the newly sorted array.
