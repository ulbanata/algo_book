# Big O Notation

When comparing different algorithms, the speed that an algorithm takes to run is considered the most important factor. But how can you tell what might be faster? For our testing, we always consider the **worst possible case**, or the case when the algorithms takes the longest. We come up with the worst case possible for our algorithm to run and determine it's speed based off of that. We become our algorithm's worst enemy, the set of data that makes it take the most time to complete. We do this because many times we don't know all of the cases our algorithm will see in the future.

So we know how we're going to test our algorithm, by using the worst case. How do we share our results? Does it make sense to have one person see how long their algorithm takes to run on their own computer and compare those times to a different algorithm ran on another person's computer? No! Even if the computers are the same make, model, have the same amount of ram, and are running the same programs, there will still be discrepancies! One computer will run a little faster than another because of a random process that stopped running in the background, or one is slightly older or hotter than another.

In order to share the results of an algorithm, we use a tool called Big O Notation. This notation allows other programmers to quickly estimate an algorithms speed and see how it might compare to a different algorithm. You will see the notation in many different sections in this book, and they will all be in some form of **O(variable)**, where the variable is how many times the program will run for the number of items in a given data set. It can be seen as a function, where the input is the number of units the algorithm is being ran on and the output is the amount of time units an algorithm takes. We're going to run over some common Big O Notations:

### O(1)

Let's start with the easiest and best Big O notation available, the constant time notation. It's notation is **O(1)**, which means that no matter how many pieces of data, the algorithm or method will take the same amount of time to run each time. An example of an O(1) method would be adding an element to the end of an array using **.push**. If the array is empty or has 1,000 or even 1,000,000 elements, it will take the same amount of time to add an item to the end of the array. It does not take more time as the size of the array grows.

### O(n)

**O(n)** is the next common Big O Notation. An algorithm with a Big O of O(n) could be said to run in **linear time**. O(n) algorithms take longer as more items are included in the data set the algorithm is working on. It increase one time unit for every additional item added. An example of this is the **.include?** method for an array. Ruby runs .include? just like a human would. It has to look at each element in the array to see if it is what you are searching for. For an empty array, you don't have to search through anything, so it takes 0 time. When you add an element to the array, it takes 1 more unit of time to search through the array. So, for a 1000 element array, you would use 1000 time units to search through it.

### O(n<sup>2</sup>)

**O(n<sup>2</sup>)** is the next Big O Notation we'll cover. It is called quadratic and it's even slower than O(n) time to run. The run time increases at the square of the number of units in the dataset that is being ran. That means that for 1 unit, the run time is 1 time unit. For 2 units, the run time is 4 time units! For 10 units, the run time is 100 time units! You can see that the runtime increases quickly. For an O(n) algorithm running on a 1000 element array, it will take 1000 time units. For an O(n<sup>2</sup>) algorithm using the same array, it will take 1,000,000 time units!

### O(log(n))

For some algorithms that use the divide and conquer methodology where they break the problem down and build it back up, the logarithmic Big O will come into play. This runtime is seen in many different search algorithms, such as a Binary Search. The runtime is less than a linear (O(n)) runtime and more than a contant (O(1)) runtime. If you think back to algebra class, a logarithm relates the solution to exponentiation to it's exponential. That means that for the equation 10^3 = 1000, the logarithm of the equation would be log<sub>10</sub>(1000) = 3. Because a computer works in binary, all of our logarithms will be a log<sub>2</sub>. Programmers shorten this to log.

The runtime for a logarithmic algorithm grows logarithmically. For a 2 element array, it would take 1 time units to run. For a 4 element array, it would take 2 time units. For 16 elements, it would take 4 time units. For 1024 elements, 10 time units. You can see that logarithmic algorithms run much faster than linear algorithms for large data sets!

### O(n*log(n))

The **O(n*log(n))** is a mix of the O(n) linear Big O and the O(log(n)) logarithmic Big O and is commonly called Log-linear. It is very common in efficient sorting algorithms, such as Merge Sort. The runtime runs between the O(n) linear time and the O(n<sup>2</sup>) quadratic time. The runtime can be found by multiplying the linear runtime by the logarithmic runtime. This means that, for a 4 element array, the runtime is 8, or 4 * 2. For a 1024 element array, the runtime is 10240, or 1024 * 10.

### O(2<sup>n</sup>)

MORE RESEARCH HERE

### O(n!)

The worst of the worst! MORE RESEARCH HERE

## Ordering the Big O's

<table>
<tr>
    <th>Notation</th>
    <th>Name</th>
</tr>
<tr>
    <td>O(1)</td>
    <td>Constant</td>
</tr>
<tr>
    <td>O(log(n))</td>
    <td>Logarithmic</td>
</tr>
<tr>
    <td>O(n)</td>
    <td>Linear</td>
</tr>
<tr>
    <td>O(n*log(n))</td>
    <td>Log-linear</td>
</tr>
<tr>
    <td>O(n<sup>2</sup>)</td>
    <td>Quadratic</td>
</tr>
<tr>
    <td>O(n<sup>c</sup>)</td>
    <td>Polynomial</td>
</tr>
<tr>
    <td>O(2<sup>n</sup>)</td>
    <td>Exponential</td>
</tr>
<tr>
    <td>O(n!)</td>
    <td>Factorial</td>
</tr>
</table>

The above table ranks the Big O Notations in order from fastest to slowest.

<table>
<tr>
    <th>Elements</th>
    <th>O(1)</th>
    <th>O(log(n))</th>
    <th>O(n)</th>
    <th>O(n*log(n))</th>
    <th>O(n<sup>2</sup>)</th>
    <th>O(n<sup>5</sup>)</th>
    <th>O(2<sup>n</sup>)</th>
    <th>O(n!)</th>
</tr>
<tr>
    <td>2</td>
    <td>1</td>
    <td>1</td>
    <td>2</td>
    <td>2</td>
    <td>4</td>
    <td>32</td>
    <td>4</td>
    <td>2</td>
</tr>
<tr>
    <td>8</td>
    <td>1</td>
    <td>3</td>
    <td>8</td>
    <td>24</td>
    <td>64</td>
    <td>32768</td>
    <td>256</td>
    <td>40320</td>
</tr>
<tr>
    <td>64</td>
    <td>1</td>
    <td>6</td>
    <td>64</td>
    <td>384</td>
    <td>4096</td>
    <td>1.1 e9</td>
    <td>1.8 e19</td>
    <td>1.3 e89</td>
</tr>
<tr>
    <td>1024</td>
    <td>1</td>
    <td>10</td>
    <td>1024</td>
    <td>10240</td>
    <td>1048576</td>
    <td>1.1 e15</td>
    <td>1.8 e308</td>
    <td>5.4 e2639</td>
</tr>
</table>

## Verbalizing Big O Notation
