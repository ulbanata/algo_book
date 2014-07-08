# Merge Sort Solution

## Recursive

```ruby
def mergesort(array)
  return array if array.length <= 1

  midpoint = array.length/2

  left_arr = mergesort(array[0..midpoint-1])
  right_arr = mergesort(array[midpoint..-1])
  merge(left_arr, right_arr)
end

def merge(left_arr, right_arr)
  sol = []
  left_counter = 0
  right_counter = 0

  until left_counter >= left_arr.count || right_counter >= right_arr.count
    if left_arr[left_counter] <= right_arr[right_counter]
      sol << left_arr[left_counter]
      left_counter += 1
    else
      sol << right_arr[right_counter]
      right_counter += 1
    end
  end

  sol + left_arr[left_counter..-1] + right_arr[right_counter..-1]
end
```

## Iterative

```ruby
def iter_mergesort(arr)
  sol = []
  arr.each do |x|
    sol << [x]
  end

  while sol.length > 1
    holder = []
    i = 0
    while i < sol.length
      if sol[i+1]
        holder << merge(sol[i], sol[i+1])
        i += 2
      else
        holder << sol[i]
        i += 1
      end
    end
    sol = holder
  end
  sol[0]
end
```
