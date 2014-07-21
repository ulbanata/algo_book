# Insertion Sort Solution

```ruby
def insertion_sort(array)
  (1...array.length).each do |i|
    j = i
    while j > 0
      if array[j] < array[j-1]
        array[j], array[j-1] = array[j-1], array[j]
        j -= 1
      else
        j = 0
      end
    end
  end
  array
end
```
