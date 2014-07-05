# Stack Level Too Deep!

For every recursive call we make in a function, we add a frame to our call stack. If you've ever accidently started up a recursive function and forgot to add your base cases, then you are all too familiar with the error `SystemStackError: stack level too deep`. This occurs when your method continuously makes recursive calls, creating too many frames for your stack to handle!

So what is going on behind the scenes? For most*** programming languages, whenever a recursive function is ran, it creates the stack. The stack has a set amount of memory allocated to it, and, if the recursive function uses more than has been allocated, a stack overflow occurs. For most methods that make a few recursive calls to solve a problem, stack overflow won't occur. For larger, harder problems that make more recursive calls, stack overflow can become a serious issue. When this occurs, there are two solutions. You can manually change stack size on the machine the code is being ran on or you can rewrite the recursive function as an iterative function.

Because we live in a world of distributed software and the world wide web, the best (and usually only) solution is to rewrite the function into an iterative function. For front-end developers and engineers, recursive functions can become a major issue. The resources that are available on the front end are usually very sparse and can quickly cause stack overflow issues. Another problem is that different browsers have very different stack allocations. You can [see here the stack allocation differences from several major browsers](http://stackoverflow.com/questions/7826992/browser-javascript-stack-size-limit).

So what's a programmer to do? As always, think about your code. What environments will it be ran in? What will it be used for? Can it potentially cause a stack overflow? How can you prevent this from happening?

If the code has the potential to cause a stack overflow, then it is usually a good idea to code an iterative solution. You just learned how to convert iterative functions into recursive functions, now how do you convert recursive functions into iterative ones?

EXAMPLE HERE>>>>>><<<<<<<<<
