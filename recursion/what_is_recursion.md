# What is Recursion?

So what is recursion? Recursion is another way of solving iterative problems. You already know how to solve a problem iteratively, using some kind of loop. Recursion is another similar tool to iteration. The best way to explain recursion is to use an example.

Let's say we're trying to find the [factorial of a number](http://en.wikipedia.org/wiki/Factorial). We can solve this iteratively using a method as such:

```ruby
def factorial(x)
  sol = 1
  (1..x).each do |num|
    sol *= num
  end
  sol
end
```

If we run `factorial(5)`, our method will return 120.

But now let's start thinking about the problem in a different format. What if we want to solve it for just the case when x is 1? We only need to return 1. Then our method would look something like this:

```ruby
def factorial(x)
  if x == 1
    1
  end
end
```

That works for x == 1, what about for x == 2?

```ruby
def factorial(x)
  if x == 1
    1
  elsif x == 2
    2 * factorial(1)
  end
end
```

Did you notice what we did for x == 2? Because we already know that our method solves the case for x == 1, we can call it and not have to do any calculations. We now have a method that works for x == 2 and x == 1. Let's include the x == 3 case.

```ruby
def factorial(x)
  if x == 1
    1
  elsif x == 2
    2 * factorial(1)
  elsif x == 3
    3 * factorial(2)
  end
end
```

Notice that for x == 3, we call on `factorial(2)`, just like we did for when x == 2. We know that our method works for x == 2, so we don't have to recalculate anything. We can repeat this process to get the case for when x == 4 and x == 5.

```ruby
def factorial(x)
  if x == 1
    1
  elsif x == 2
    2 * factorial(1)
  elsif x == 3
    3 * factorial(2)
  elsif x == 4
    4 * factorial(3)
  elsif x == 5
    5 * factorial(4)
  end
end
```

We can use this to call `factorial(5)` like we did earlier, getting back 120! But what happens if we want to call `factorial(1000)`? That would be 1000 elsif statements! That's way too many to write out! But did you notice a pattern? For every if statement we have, if the statement is true, we run `x * factorial(x - 1)`. We can use that to refactor our method into a recursive version!

```ruby
def factorial(x)
  return x if x <= 1
  x * factorial(x - 1)
end
```

That's it! Just two lines to rewrite the method.
