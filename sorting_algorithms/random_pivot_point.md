# Random Pivot Point

```ruby
def quick_sort_rand(array)
  return array if array.length <= 1
  i = 0
  j = array.length - 2
  pivot_point = rand(array.length)
  # p pivot_point
  array[pivot_point], array[-1] = array[-1], array[pivot_point]
  pivot = array[-1]
  # p "pivot #{pivot}"
  while i != j
    if array[i] < pivot
      i += 1
    elsif array[i] > pivot
      array[j], array[i] = array[i], array[j]
      j -= 1
    else
      i += 1
    end
  end
  if array[j] > array[-1]
    array[j], array[-1] = array[-1], array[j]
  else
    i = j += 1
    array[j], array[-1] = array[-1], array[j]
  end

  left = quick_sort_rand(array[0...i])
  # p left
  # p pivot
  right = quick_sort_rand(array[i+1..-1])
  # p right
  left + [pivot] + right
end
```
