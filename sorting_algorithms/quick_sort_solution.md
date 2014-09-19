# Quick Sort Solution
```ruby
def quick_sort(array)
  return array if array.length <= 1
  i = 0
  j = array.length - 2
  pivot = array[-1]
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

  left = quick_sort(array[0...i])
  # p left
  # p pivot
  right = quick_sort(array[i+1..-1])
  # p right
  left + [pivot] + right
end
```





