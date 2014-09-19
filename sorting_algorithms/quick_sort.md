# Quicksort

### Non-stable and Adaptive\* - O(n<sup>2</sup>) (Usually  O(n\*log(n))

Quicksort is the sorting algorithm that runs many of the built-in sorts that you run into while programming, including Ruby's `.sort` method. The quicksort algorithm has an **O(n*log(n))** runtime for most cases, but the worst case is **O(n<sup>2</sup>)**. So why would we use this algorithm? The reasoning behind it is that for almost all searches, quicksort is faster than mergesort. This occurs because of the way caching works in a computer and is beyond the scope of this book. However, we are still going to take a look at the algorithm behind quicksort.

Quicksort is an algorithm that
