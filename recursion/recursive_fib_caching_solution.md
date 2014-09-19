# Recursive Fib Caching Solution

```ruby
class Fibonacci
  @@cache = {}

  def self.num(n)
    return @@cache[n] if @@cache[n]
    return 1 if n <= 2
    sol = self.num(n-1) + self.num(n-2)
    @@cache[n] = sol
  end
end
```

The above is a solution to the Recursive Fibonacci Caching Challenge. It creates a Fibonacci class that has a class variable called `@@cache` that keeps track of the cache of fibonacci numbers. We'll break down the method `self.num`.

`return @@cache[n] if @@cache[n]`

This line checks the cache and, if n is already in the cache, will return its result. This is the line that greatly speeds up our entire algorithm. If n isn't in the cache and isn't 1 or 2, then it will have to make the two recursive calls.

```ruby
return 1 if n <= 2
sol = self.num(n-1) + self.num(n-2)
```

These two lines are doing the same thing as we had for our recursive fibonacci sequence earlier. Nothing has changed with them.

`@@cache[n] = sol`

This line will save the solution to the cache once it has been found, so we don't have to recalculate the solution in the future.

Now when we run `Fibonacci.num(50)`, it runs very quickly, because its new runtime is O(n)! Notice, though, that for a large enough number (For me, anything over 5000) the stack overflow error will be called. Our caching solution works, but it would be better if we didn't use recursion to begin with.

