# FizzBuzz Recursive Solution

Many people, when first asked to solve this problem, want to create a helper method that takes a counter to keep track of where they should stop the fizzbuzz method at. I have seen a lot of methods that look like the one below:

```ruby
def fizzbuzz(n)
  helper_fizzbuzz(n, 1)
end

helper_fizzbuzz(n, x)
  if x % 15 == 0
    puts fizzbuzz
  elsif x % 3 == 0
    puts fizz
  elsif x % 5 == 0
    puts buzz
  else
    puts x
  end

  helper_fizzbuzz(n, x + 1) unless x == n
end
```

While this works, it makes the problem more complicated then it needs to be. All the fizzbuzz method does is call the helper method with an extra parameter. The reason that most people can't see how they might print the numbers out in ascending order. Remember the countdown problem? Our solution ended up being this:

```ruby
def countdown(n)
  puts n

  if n > 0
    countdown(n-1)
  end

end
```

The puts statement came before our recursive call. This resulted in us counting down from n to 0. What happens if we put the puts statement below our recursive call? Remember in Ruby that each line has to be solved before the next one can be ran. That means that all recursive calls made by a method, if the recursive call comes before the puts, would have to be solved before the puts statement was ran. Lets look at a countup method, a method that will count from 0 to n:

```ruby
def countup(n)
  if n > 0
    countup(n - 1)
  end

  puts n
```

That's all it takes to count up from 0 to n versus counting down from n to 0. **The only difference between counting down and counting up is where we put our recursive call in relation to our puts statement!**

Using that information, here is a single method solution to fizzbuzz that counts up:

```ruby
def fizzbuzz(n)
  fizzbuzz(n - 1) if n > 1

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
```
