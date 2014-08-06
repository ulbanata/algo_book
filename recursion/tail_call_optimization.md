# Tail Call Optimization

Tail Call Optimization is a term that you may run across in your future as a web developer. It is a way to optimize recursive functions that improves their efficiencies **for certain programming languages**. The optimization occurs by cutting down on the number of frames in the call stack, which reduces the amount of memory being used. Sadly, Ruby does not have this feature, but I will give you an idea of how it works.

Let's take a look at the factorial recursive function again:

```ruby
def factorial(x)
  return x if x <= 1
  x * factorial(x - 1)
end
```

If we break down what occurs during the recursive call, we start a call stack. This call stack, for x = 5, would have 5 frames.

# Images of call stack here

What happens if we didn't have to keep the information in the first frame (where x = 5)? If we could get rid of it as soon as we make the recursive call for x = 4, our method would save memory! But right now, our method needs every other factorial to solve before we can discover the answer of factorial(5).

Let's see what happens if we change it a little bit:

```ruby
def factorial(x, cur_sol=1)
  return x * cur_sol if x <= 1
  factorial(x-1, x*cur_sol)
end
```

What's different here? Instead of needing to climb back up our call stack, whenever we get to the function call for x = 1, we already know the solution! Our method can exit here and ignore the remainder of the frames in the call stack. This is Tail Call Optimization. Every recursive function call that is made contains all information that is needed from the current frame! Here is what the call stack could then look like:

# Images of tail call call stack here

So this means that for every recursive function call that
is made, the frame that the call is being made from is now not important! For x = 5, once the recursive call of factorial(4, 5) is made, then the frame containing the information for factorial(5) can be deleted! No more memory leaks!

So, if this fixes the problems with recursive calls, why doesn't Ruby use it? It is because Ruby's interpreter is a "dumb" interpreter. If you remember how Ruby runs your code, it reads it one line at a time. Ruby can't tell that your function has a tail call optimization in it because it only sees one line of code!
