# Radix Sort

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
