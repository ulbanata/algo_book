# The Fibonacci Sequence and Recursion - A Cautionary Tale

First, let's recap what the Fibonacci sequence is:

The Fibonacci sequence is 1, 1, 2, 3, 5, 8, 13, 21, 34, 55, 89, 144, ...
The nth Fibonacci number is the nth number in the sequence. For example, the 4th number (for n = 4) is 3. The 7th number is 13. The 11th number is 89. In order to get the nth number in the sequence, you add up the two preceding numbers in the sequence, n-1 and n-2. So, to get the 12th number in the sequence, we add together the 11th number and the 10th number. This results in 55 + 89 = 144. The first two numbers (the "seed" numbers) are 1 and 1 (Or, in some cases, 0 and 1). Below is a table of the Fibonacci sequence, showing the relationships. You can find out more about the [Fibonacci sequence here](http://en.wikipedia.org/wiki/Fibonacci_number).

<table>
    <tr>
        <th>nth #</th>
        <th>Fib #</th>
        <th>n-1 + n-2 to get Fib #</th>
    </tr>
    <tr>
        <td>1</td>
        <td>1</td>
        <td>N/A (Seed Number)</td>
    </tr>
    <tr>
        <td>2</td>
        <td>1</td>
        <td>N/A (Seed Number)</td>
    </tr>
    <tr>
        <td>3</td>
        <td>2</td>
        <td>1 + 1 (2nd Fib # + 1st Fib #)</td>
    </tr>
    <tr>
        <td>4</td>
        <td>3</td>
        <td>2 + 1 (3rd Fib # + 2nd Fib #)</td>
    </tr>
    <tr>
        <td>5</td>
        <td>5</td>
        <td>3 + 2 (4th Fib # + 3rd Fib #)</td>
    </tr>
    <tr>
        <td>6</td>
        <td>8</td>
        <td>5 + 3 (5th Fib # + 4th Fib #)</td>
    </tr>
    <tr>
        <td>7</td>
        <td>13</td>
        <td>8 + 5 (6th Fib # + 5th Fib #)</td>
    </tr>
        <tr>
        <td>8</td>
        <td>21</td>
        <td>13 + 8 (7th Fib # + 6th Fib #)</td>
    </tr>
        <tr>
        <td>9</td>
        <td>34</td>
        <td>21 + 13 (8th Fib # + 7th Fib #)</td>
    </tr>
        <tr>
        <td>10</td>
        <td>55</td>
        <td>34 + 21 (9th Fib # + 8th Fib #)</td>
    </tr>
        <tr>
        <td>11</td>
        <td>89</td>
        <td>55 + 34 (10th Fib # + 9th Fib #)</td>
    </tr>
</table>

What algorithm could we write to return the nth Fibonacci number? We have two seed numbers, 1 and 1. Let's start with them.

```ruby
def fib(n)
seed_a = 1
seed_b = 1
end
```

Now, in order to get the 3rd Fibonacci number, we can just add `seed_a` and `seed_b` together. But right now we can't go higher than that. If we look at the table above, we can start to see a pattern on how to get a Fibonacci number. If we start from the bottom, with 1 and 1, we can loop through all the Fibonacci numbers to the number we need. Let's add that in.

```ruby
def fib(n)
    x = 1
    y = 1
    (3..n).each do |nth_number|
        y, x = y + x, y
    end
    y
end
```

Ruby Note: The `y, x = y + x, y` line above is the [Ruby Multiple Assignment](http://nathanhoad.net/ruby-multiple-assignment). It is doing the same thing as
```ruby
holder = y
y = y + x
x = holder
```

Finally, we add in the edge cases of the 1st or 2nd number being inputted. (We are assuming only positive integers can be inputted)

```ruby
def fib(n)
    return 1 if n <= 2
    x = 1
    y = 1
    (3..n).each do |nth_number|
        y, x = y + x, y
    end
    y
end
```

We have a working algorithm that will return the nth Fibonacci number! Though it looks messy. Let's see what would happen if we used recursion to rewrite it:

```ruby
def rec_fib(n)
    return 1 if n <= 2
    rec_fib(n - 1) + rec_fib(n - 2)
end
```

That looks much cleaner! The recursive solution for the fibonacci number is only 4 lines compared to the 9 lines we need for the iterative solution. Line 2 contains the base case and line 3 contains the recursive case. Why would we not use this?

For those adventurous souls that want to see what happens when we use the two different methods, try tossing them into your console. First run the iterative solution for 10, 50, 100, 1000 and 10000. Notice how fast the program runs? Now try it with the recursive solution. If your console freezes while running, you should be able to use ctrl + c to kick it out of the code it is currently executing.

Unless you're on a supercomputer, running `rec_fib(50)` probably took a long time. Why? The problem it's solving is the same as the recursive solution, but running `fib(50)` seems almost instantaneous! Why does the recursive solution take so long?

To solve this problem, let's take a look at what is happening for small nth Fibonacci numbers. For the 1st and 2nd Fibonacci numbers, the method returns `1` on the first line. No recursive calls are made. For the 3rd fibonacci number, it makes the recursive call. It runs `rec_fib(2)` and `rec_fib(1)`, which returns `1` without any recursive calls. The problem still isn't visible.

![Image goes here]()

So what happens when we run `rec_fib(4)`? We run the recursive calls `rec_fib(3)` and `rec_fib(2)` to find the 4th number. We already know that `rec_fib(3)` runs the recursive calls `rec_fib(2)` and `rec_fib(1)`. We're calling `rec_fib(2)` twice! But is that the problem? `rec_fib(2)` only returns 1.

![Image goes here]()

What about `rec_fib(5)`? It calls `rec_fib(4)` and `rec_fib(3)`. We know that `rec_fib(4)` calls `rec_fib(3)` and `rec_fib(2)`. Wait, now we're calling `rec_fib(3)` twice! And now `rec_fib(2)` is getting called three times!

![Image goes here]()

It looks like for large nth numbers, we're running the same method calls multiple times. Multiple calls on the same method can become a problem quickly. But in this case how quickly does it become a problem? I did a little benchmarking using [Ruby's Benchmark module](http://www.ruby-doc.org/stdlib-1.9.3/libdoc/benchmark/rdoc/Benchmark.html) and here are the results:

<table>
    <tr>
        <th>n</th>
        <th>fib(n) time (s)</th>
        <th>rec_fib(n) time (s)</th>
    </tr>
    <tr>
        <td>10</td>
        <td>0.000</td>
        <td>0.000</td>
    </tr>
    <tr>
        <td>20</td>
        <td>0.000</td>
        <td>0.001</td>
    </tr>
    <tr>
        <td>30</td>
        <td>0.000</td>
        <td>0.105</td>
    </tr>
    <tr>
        <td>40</td>
        <td>0.000</td>
        <td>12.508</td>
    </tr>
    <tr>
        <td>50</td>
        <td>0.000</td>
        <td>1560.880</td>
    </tr>
</table>

As you can see, the recursive solution slows down within the first 50 fibonacci numbers, while the iterative solution is so fast, it can compute in less than a millisecond! Looking up the 50th fibonacci number recursively takes a full 26 minutes to complete!

So what is the Big O notation of the two solutions? We'll start with the iterative solution. Looking at the method, we can see that for an input of 1 or 2, the Big O is O(1). But for any other case, we have to iterate once through the numbers from 3 to n. If you remember back to chapter 3, a single interation is associated with O(n) time. So, the worst case for the iterative solution of the Fibonacci number is O(n).

What about for the recursive solution? This one is much tougher to figure out and uses a Big O notation that you probably haven't seen before. Let's break down what's going on for each line.

```ruby
return 1 if n <= 2
```

This line is the simple case. It is O(1).

```ruby
rec_fib(n - 1) + rec_fib(n - 2)
```

Here is the tough line. What are the Big O's of the recursive calls `rec_fib(n - 1)` and `rec_fib(n - 2)`? We can solve this by thinking recursively again! Let's say we call `rec_fib(3)`. This method call ends up with two recursive calls, `rec_fib(2)` and `rec_fib(1)`. We know that for both of the two recursive calls, they run in O(1) time. So the Big O of `rec_fib(3)` is the sum of the Big O's of the two recursive calls.  Let's build a table to see what is happening:

<table>
<tr>
    <th>n</th>
    <th>Big O</th>
</tr>
<tr>
    <td>1</td>
    <td>1</td>
</tr>
<tr>
    <td>2</td>
    <td>1</td>
</tr>
<tr>
    <td>3</td>
    <td>2</td>
</tr>
<tr>
    <td>4</td>
    <td>3</td>
</tr>
<tr>
    <td>5</td>
    <td>5</td>
</tr>
<tr>
    <td>6</td>
    <td>8</td>
</tr>
<tr>
    <td>7</td>
    <td>13</td>
</tr>
<tr>
    <td>8</td>
    <td>21</td>
</tr>
</table>

Notice anything familiar? The Big O expands just like the Fibonacci Sequence! That means that for the recursive solution, we have O(fib(n))! That's why the recursive solution is taking so long to complete. The 50th Fibonacci number is 12586269025. The iterative solution only needs to take 50 units of time because it is O(n), while the recursive solution takes 12586269025 units of time because it is O(fib(n))! If you want a more detailed, mathy response, you can look [here](http://stackoverflow.com/questions/360748/computational-complexity-of-fibonacci-sequence) and [page 5 here](http://courses.csail.mit.edu/6.01/spring07/lectures/lecture4.pdf).

With all that being said, does this mean recursion is always the wrong way? No! Recursion is a very helpful way to solve many different problems.
