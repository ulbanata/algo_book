# FizzBuzz Recursion

The FizzBuzz problem is a coomon one in technical interviews. It tests the interviewees control over loops and conditionals and knowledge of modulos. The questions goes something like this:

"Write a method that takes a number, n. The method will then print out all numbers from 1 to n. However, instead of printing a multiple of 3, the method will print fizz. Instead of a multiple of 5, the method will print buzz. If a number is both a multiple of 3 and 5, the method will print fizzbuzz."

If 17 is passed into the method, it would print out this:
`1 2 fizz 4 buzz 5 fizz 7 8 fizz buzz 11 fizz 13 14 fizzbuzz 16 17`

An iterative solution could look something like this:

```ruby
def fizzbuzz(n)
  (1..n).each do |x|
    if x % 15 == 0
      puts fizzbuzz
    elsif x % 3 == 0
      puts fizz
    elsif x % 5 == 0
      puts buzz
    else
      puts x
    end
  end
end
```

The solution is rather straightforward. It runs through all numbers from 0 to n. It then checks to see if each number is a multiple of 15, 3 or 5. If so, it prints out "fizzbuzz", "fizz" or "buzz", respectively. Otherwise, it prints out the number.

How would you print out fizzbuzz recursively? Try to do it using only one method.
