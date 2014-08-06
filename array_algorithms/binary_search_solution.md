# Binary Search Solution

Recursive Solution:
```ruby
def binary_search(arr, search_term)
  return false if arr.length <= 0

  midpoint = arr.length/2
  return true if arr[midpoint] == search_term
  if search_term < arr[midpoint]
    binary_search(arr[0...midpoint], search_term)
  else
    binary_search(arr[midpoint+1..-1], search_term)
  end

end
```

Iterative Solution:
```ruby
def binary_search(arr, search_term)
  return false if arr.length == 0

  midpoint = arr.length/2
  lower = 0
  upper = arr.length - 1
  until lower == upper
    return true if arr[midpoint] == search_term
    if search_term < arr[midpoint]
      upper = midpoint - 1
    else
      lower = midpoint + 1
    end
    midpoint = lower + (upper - lower)/2
  end

  return true if arr[midpoint] == search_term
  false
end
```

