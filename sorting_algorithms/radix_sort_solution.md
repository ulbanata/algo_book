# Radix Sort Solution

```ruby
def radix_sort(arr)
  (0...num_passes(arr.max)).each do |i|
    buckets = Array.new(10) {[]}
    arr.each do |num|
      buckets[get_digit(num, i)] << num
    end
    arr = buckets.flatten
  end
  arr
end

def get_digit(num, digit_num)
  (num / (10**digit_num)) % 10
end

def num_passes(num)
  num.to_s.length
end
```

Before we jump into the `radix_sort` method, let's take a look at the other two methods that are included. The first, `get_digit`, takes a number that we are grabbing the digit from (`num`), and the digit we are wanting (1 for the 1's place, 2 for the 10's place, 3 for the 100's place, etc.). The method grabs the digit we are interested in by first reducing the num to where the digit we want is in the 1's place by running `(num / (10**digit_num))`. If we want the 1's place of the number 487, this part of the method will return 487. If we want the 10's place, it would return 48. Now, when we take the modulo of the 487 by 10, then it will return 7. If we want the 10's digit, it will result in `48 % 10`, which returns 8.

`num_passes` is a method that determines the maximum number of digits a number has in the array. This way we can determine how many times to sort based on the places.

```ruby
def radix_sort(arr)
  (0...num_passes(arr.max)).each do |i|
    buckets = Array.new(10) {[]}
    arr.each do |num|
      buckets[get_digit(num, i)] << num
    end
    arr = buckets.flatten
  end
  arr
end
```

The `radix_sort` method

