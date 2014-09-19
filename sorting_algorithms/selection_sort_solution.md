# Selection Sort Solution

```ruby
def selection_sort(arr)
  arr.each_index do |swap_loc|
    min_loc = swap_loc
    ((swap_loc+1)..(arr.length - 1)).each do |curr_index|
      if arr[curr_index] < arr[min_loc]
        min_loc = curr_index
      end
    end
    arr[swap_loc], arr[min_loc] = arr[min_loc], arr[swap_loc]
  end
end
```

<!-- Need better variable names? -->

The code for selection sort is relatively short. We know that we need to touch each element in the array at least once, so using a `.each` makes sense. However, because we want to swap the values of two different elements, using a `.each_index` works better. This allows us to know where the element we are looking at is in the array at all times. This index is stored in the variable `swap_loc`.

The `min_loc` stores the current location of the minimum element. We then need another iterator to move through the array. This is accomplished with the use of a `.each` on a range from the `swap_loc` to the end of the array.

The `if` statement within this inner `.each` checks to see if the current element that is being looked at is smaller than the current smallest value. If it is, then the location of the minimum, stored in `min_loc` is updated to the current number.

Once outside of the inner loop, the swap occurs. The element that is occupying the `swap_loc` is moved to the position of the `min_loc` in the array and vice-versa. This continues until every element in the array has been touched by the outer `.each_index` loop.

