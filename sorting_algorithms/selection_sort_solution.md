# Selection Sort Solution

```ruby
def selection_sort(arr)
  arr.each_index do |swap_loc|
    min_loc = swap_loc
    ((swap_loc+1)..(arr.length - 1)).each do |x|
      if arr[x] < arr[min_loc]
        min_loc = x
      end
    end
    arr[swap_loc], arr[min_loc] = arr[min_loc], arr[swap_loc]
  end
end
```

## Need better variable names, especially for x
