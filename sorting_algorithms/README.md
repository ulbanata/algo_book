# Sorting Algorithms

Sorting is traditionally the first set of algorithms that students start learning about. Sorting algorithms have many uses and are relatively easy to build. There are many different types of sorting algorithms, from easy to implement but very slow algorithms, to complex but fast algorithms. There are also specialized versions of sorting algorithms for certain cases, such as radix sort.
The many use cases and differing types make sorting algorithms extremely interesting to study. We use numbers in our algorithms, but they can be used to sort anything.

That being said, when using Ruby, the built in `.sort` method is extremely optimized. `.sort` will (probably) beat any sorting algorithm that you might come up with because of its heavy optimization and the fact that it is written in C.

The first three algorithms we will cover, selection sort, insertion sort, and bubble sort, are very similar in how they operate. The details help to speed up the algorithm for specific cases. Merge sort is the next algorithm that we will cover, and it uses the idea of divide and conquer to sort. Next comes Quick Sort, which uses another take on divide and conquer to solve the sorting problem. Finally, Radix Sort is a specialized sorting algorithm that exploits low digit numbers to sort in a fast runtime.

There are two characteristics of sorting algorithms that we will also cover:
* Adaptibility
* Stability

Adaptive sorting algorithms are sorts that adapt to almost sorted arrays. This is a very good characteristic to have and adaptive algorithms can speed up their runtimes from O(n<sup>2</sup>) to almost O(n) runtime! This is contrasted by non-adaptive sorting algorithms, which cannot determine if an array is already sorted, and, therefore, take much longer time to sort the array.

When I first saw that the sort a sort could be stable or non-stable, I thought that this meant non-stable sorts could end up taking infinite time. Thankfully, I was wrong. Stable sorts are sorts that keep elements with the same value in the same order they had before sorting. This is important for objects that are being sorted for varying characteristics. Let's use an example of a Person class.

```ruby
class Person
  attr_reader :name, :age
  def initialize(name, age)
    @name = name
    @age = age
  end
end
```

Here are some instances of our Person class in an array:
```ruby
[<Person: @name="Patrick", @age=25>,
<Person: @name="Jane", @age=25>,
<Person: @name="John", @age=26>,
<Person: @name="Corey", @age=24>]
```
We want to put everyone in order by age, alphabetically. Our final array should look like this:

```ruby
[<Person: @name="Corey", @age=24>,
<Person: @name="Jane", @age=25>,
<Person: @name="Patrick", @age=25>,
<Person: @name="John", @age=26>]
```

We'll sort the array in alphabetical order first:
```ruby
[<Person: @name="Corey", @age=24>,
<Person: @name="Jane", @age=25>,
<Person: @name="John", @age=26>,
<Person: @name="Patrick", @age=25>]
```

Now we want everyone in order by age, but the order of our array could depend on if our sort is stable or not. A stable sort would give us the array in the sorted format we would like. However, a non-stable sort could return this:

```ruby
[<Person: @name="Corey", @age=24>,
<Person: @name="Patrick", @age=25>,
<Person: @name="Jane", @age=25>,
<Person: @name="John", @age=26>]
```

[Sorting Algorithm Visualizations](sorting-algorithms.com)
