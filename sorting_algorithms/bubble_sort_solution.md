# Bubble Sort Solution

<!-- Needs better variable names!!!-->

```ruby
def bubble_sort(array)
  arr = array.dup
  last_swapped = 1
  while last_swapped < arr.length
    watcher = arr.length
    (arr.length - 1).downto(last_swapped) do |index|
      if arr[index] < arr[index - 1]
        arr[index], arr[index - 1] = arr[index - 1], arr[index]
        watcher = index
      end
    end
    last_swapped = watcher + 1
  end
  arr
end
```

