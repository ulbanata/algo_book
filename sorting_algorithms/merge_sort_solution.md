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

You can see that the above solution has two different methods. One is the mergesort method that takes the array to be sorted. The other is the merge method we talked just talked about. Let's break down the merge method first.

### Merge Method

```ruby
def merge(left_arr, right_arr)
  sol = []
  left_counter = 0
  right_counter = 0
```

We are assuming that the two arrays we are receiving are already sorted. If we have to check to see if they are sorted before we work with them, then it will be faster to use a different sort (Checking to see if something is sorted takes O(n) time to complete)! The merge method sets three variables initially, the solution array, which will be returned, and two counters for the two arrays that are passed in.

```ruby
  until left_counter >= left_arr.count || right_counter >= right_arr.count
    if left_arr[left_counter] <= right_arr[right_counter]
      sol << left_arr[left_counter]
      left_counter += 1
    else
      sol << right_arr[right_counter]
      right_counter += 1
    end
  end
```

The `until` loop is where most of the work takes place. It runs until one of the counters has reached the end of one of the two arrays that were passed in. Until that occurs, this loop determines which pointer is pointing to the smaller number and pushes that number to the solution array. It then increments the counter that held the smaller number by 1.

```ruby
  sol + left_arr[left_counter..-1] + right_arr[right_counter..-1]
end
```

Once a counter reaches the end of an array, the remaining numbers are added to the end of the solution array through concatenation. Then the solution array is returned using implicit returns.

If you are still unsure about what the merge method code is trying to do, review the merge method section just before this one!

### Mergesort Method

```ruby
def mergesort(array)
  return array if array.length <= 1
```


The mergesort method is more straightforward. The first line is our base case. If an array is inserted into the mergesort method that has 1 or 0 elements, then the array is instantly returned.
```ruby
  midpoint = array.length/2
```

We then find the midpoint of the array. This midpoint is used to split the two arrays in half.

```ruby
  left_arr = mergesort(array[0..midpoint-1])
  right_arr = mergesort(array[midpoint..-1])
  merge(left_arr, right_arr)
end
```

Next, the recursive calls are made. The array is split in half and the mergesort method is called on it again. Pay careful attention to how we split the arrays. We grab all elements left of the midpoint for the left array and all elements to the right of the midpoint and including the midpoint for our right array. If we had used `array[0..midpoint]` instead, then our split would result in an infinite loop for two element arrays. This is because the left array would contain the 2 elements and the right array would contain 0 elements.

The resulting sorted arrays are stored in two variables and they are merged using the merge method. The result of the merge method is the sorted array.


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

The iterative solution is less elegant than the recursive solution and is probably not necessary. For most number sets, the recursive solution will work. For those times when recursion will not work, however
