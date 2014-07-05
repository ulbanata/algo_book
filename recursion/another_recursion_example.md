# Another Recursion Example

Below is another example of changing an iterative method into a recursive one.

Let's say that we're going to write a method that takes in a number as a parameter and counts down from that number to 0. We can easily do this iteratively with any kind of loop. Here is one example of an iterative solution:

```ruby
def countdown(n)
  while n >= 0
    puts n
    n -= 1
  end
end
```

Let's start thinking about the problem from a different point of view. Let's start with a method that only works for inputting 0.  Here's what it might look like:

```ruby
def countdown(n)
  puts n
end
```

This only works for the case when n == 0. Now let's think about what to do for n == 1.

```ruby
def countdown(n)
  puts n
  if n == 1

  end
end
```

What should we put in the if statement? What should be run? We already know that our countdown method works for when n == 0, so we could just call it again! Now our method looks like:

```ruby
def countdown(n)
  puts n

  if n == 1
    countdown(0)
  end
end
```

That's two cases down! Now what about for when n == 2? What do we have to do in that case? We already know that the method works for n == 1, so we can add a new if statement for the case n == 2!

```ruby
def countdown(n)
  puts n

  if n == 1
    countdown(0)
  end

  if n == 2
    countdown(1)
  end
end
```

This can repeat for n == 3 as well!

```ruby
def countdown(n)
  puts n

  if n == 1
    countdown(0)
  end

  if n == 2
    countdown(1)
  end

  if n == 3
    countdown(2)
  end
end
```

Starting to see the pattern? But this approach isn't very sustainable. If someone wants to countdown from 1000, that would be 1000 if statements, and no one wants to write that. So what exactly is the pattern? For each if, if the statement is true, we call the countdown method again, but we pass in the number - 1. Let's use that to make our method more readable.

```ruby
def countdown(n)
  puts n

  if n > 0
    countdown(n-1)
  end

end
```

That's all it takes!
