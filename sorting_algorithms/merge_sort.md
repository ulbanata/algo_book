# Merge Sort

Merge sort is a very efficient sort that breaks down the problem to its smallest part before building it back up. The base version uses recursion in order to solve the sorting problem.

Before we begin going through recursion, let's think about how we can break this problem up into smaller parts. How long does it take to sort an array with 8 elements? Currently, we have algorithms that sort in O(n<sup>2</sup>) time, so an 8 element array would take up to 64 operations to run. What if we split the array in half? How long does it take to sort a 4 element array? It takes 16 operations. That's 1/4 the time it takes to sort an 8 element array! If we have two 4 element arrays from our original 8 element array, then it takes 2 * 16 operations to sort the two arrays, or 1/2 the time to sort the 8 element array.

We can continue breaking up the arrays into smaller pieces. An array of 2 elements takes 4 operations to sort. To sort all four 2 element arrays from the original 8 element array, it will take 16 operations. That's 1/4 the number of operations!

If we have arrays with 2 elements, we can split those as well. The nice thing about 1 element arrays is that they are already sorted! So, to sort the array, we just have to check that the length is 1, so 1 operation per array. For the eight 1 element arrays that make up the original array, it will take 8 operations to make sure that everything is sorted.

<table>
<tr>
    <th>n Element Array</th>
    <th>Operations to Sort</th>
    <th># of Arrays</th>
    <th>Total # Operations</th>
</tr>
<tr>
    <td>8</td>
    <td>64</td>
    <td>1</td>
    <td>64</td>
</tr>
<tr>
    <td>4</td>
    <td>16</td>
    <td>2</td>
    <td>32</td>
</tr>
<tr>
    <td>2</td>
    <td>4</td>
    <td>4</td>
    <td>16</td>
</tr>
<tr>
    <td>1</td>
    <td>1</td>
    <td>8</td>
    <td>8</td>
</tr>
</table>

That's great and all, but how do we merge the sorted arrays together? Won't that take a lot of time? We can merge two sorted arrays together in O(n) time! We will get into the merge method a little later.

Time to visualize how Merge Sort works. We'll break down the array below into its individual components and then merge it back together.

![Split Part 1](http://i.imgur.com/WqpMPQX.png)

We're going to sort the above array using Merge Sort. Because the array size is larger than 1, we're going to split it.

![Split Part 2](http://i.imgur.com/nh5oQeK.png)

After splitting the array, we have two different arrays. The arrays are color-coded to show what "group" they are with as we continue to split. The two arrays have a length of greater than 1, so let's split again.

![Split Part 3](http://i.imgur.com/9KjskAI.png)

The arrays are now 4 arrays with 2 elements. Let's split one more time to get 8 arrays of 1 element each.

![Split Part 4](http://i.imgur.com/7Et6IF1.png)

At this point, we have all of our arrays with 1 element. It's time to start merging them together. The first merge will merge into 4 sorted arrays of 2 elements each.

![Merge Part 1](http://i.imgur.com/oP5ayoR.png)

You'll notice that the split groups that were color-coded are being merged together again. The only difference is that this time they are sorted. We continue merging the 2 element arrays into two 4 element sorted arrays.

![Merge Part 2](http://i.imgur.com/Sk8Eeh1.png)

Our arrays are back to 4 elements each, completely sorted. Let's merge one more time to get our final sorted array.

![Merge Part 3](http://i.imgur.com/X5Nx8G2.png)

At the end of our merge sort, we have sorted our original array.
