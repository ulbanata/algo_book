# Binary Search Solution

### Recursive Solution:
```ruby
def binary_search(arr, search_term)
  return false if arr.length == 0

  midpoint = arr.length/2
  return true if arr[midpoint] == search_term
  if search_term < arr[midpoint]
    binary_search(arr[0...midpoint], search_term)
  else
    binary_search(arr[midpoint+1..-1], search_term)
  end

end
```

`binary_search` is a method that takes in an array and what you are searching for. The first line in the method, `return false if arr.length == 0`, is a base case. If the array has no elements, then the item you are searching for cannot be in the array.

`midpoint = arr.length/2` finds the midpoint of the array. If the array has an even number of elements, then it finds the ceiling of the midpoint. If there is only 1 element in the array, the midpoint will point to the ***0th*** index.

`return true if arr[midpoint] == search_term`

This line checks to see if the midpoint contains our search term. If it does, the method returns true. This is another base case.

```ruby
  if search_term < arr[midpoint]
    binary_search(arr[0...midpoint], search_term)
  else
    binary_search(arr[midpoint+1..-1], search_term)
  end
```

The if/else statement determines if the method should search to the left or the right of the current midpoint. If the item we are searching for is smaller than the item located at the midpoint, a recursive call is made on the remaining left half of the array. Otherwise, a recursive call is made on the remaining right half of the array.

### Iterative Solution:
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

