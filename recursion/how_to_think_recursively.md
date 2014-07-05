# Recursive Method Internals

Whenever you work with anything in Ruby, and most other languages, you are working with something called the **call stack**. The call stack is a record of all of the different methods that are called whenever you run a line of code.

The ever popular and helpful [stackoverflow.com](http://www.stackoverflow.com) takes it's name from a problem that is easy to run into in recursion. If you've tried to write some recursive functions, you've probably ran into this error once before. It occurs when your recursive function dives too deeply, calling too many additional methods.
