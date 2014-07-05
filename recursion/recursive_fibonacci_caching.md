# Recursive Fibonacci Caching Challenge

In the recursion chapter, we learned how recursion isn't always the best answer. The recursive fibonacci method ended up taking a much longer time to complete than the iterative version. Your challenge is to take the idea of caching and apply it to the recursive fibonacci method to make its runtime be similar to the iterative fibonacci method. What can you use to cache your fibonacci numbers and speed up the process?

Here is the code for recursive fibonacci:

```ruby
def rec_fib(n)
    return 1 if n <= 2
    rec_fib(n - 1) + rec_fib(n - 2)
end
```
