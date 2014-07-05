# The Merge Method

The merge method is half of the merge sort and possibly the most important part. We already saw that we could break down the arrays into individual elements easily, but how do we merge them back together? The method needs to run in O(n) time or the merge sort won't work as efficiently as we need it to.

![Merge Part ](http://i.imgur.com/9SVAKLT.png)

We're going to merge the two above arrays together into a single sorted array. Notice that both arrays are already sorted when they are entered into the method! The merge method won't work if we try to use unsorted arrays.

![Merge Part ](http://i.imgur.com/vVNHn75.png)

To keep track of our current location, we're going to be using two pointers, one for each array. We won't be using .shift to grab the first number, because that would be an O(n) method to run. Using pointers allows us to copy values in O(1) time.

The algorithm will compare the two values the two pointers are pointing to. Whichever is lower is the one that should be added to the solution array first.

![Merge Part ](http://i.imgur.com/mIeTc7O.png)

We compared 1 against 3 and determined that 1 was smaller than 3. Because of this, we add 1 to our solution array, **sol**, and moved the pointer that had been pointing to 1 to now point at the next element, which holds 2. We continue this process.

![Merge Part ](http://i.imgur.com/YYcy2M9.png)

2 is smaller than 3, so 2 is added to the sol array and we move the pointer that had been pointing at 2 to the next element.

![Merge Part ](http://i.imgur.com/EiKI8c6.png)

3 is smaller than 5, so 3 is added to the sol array and we move the pointer that had been pointing at 3 to the next element.

![Merge Part ](http://i.imgur.com/w0UZu84.png)

4 is smaller than 5, so 4 is added to the sol array and we move the pointer that had been pointing at 4 to the next element.

![Merge Part ](http://i.imgur.com/W6SxOpa.png)

5 is smaller than 7, so 5 is added to the sol array and we move the pointer that had been pointing at 5 to the next element.

![Merge Part ](http://i.imgur.com/ViUZXiy.png)

7 is smaller than 9, so 7 is added to the sol array and we move the pointer that had been pointing at 7 to the next element.

![Merge Part ](http://i.imgur.com/tZobiDM.png)

8 is smaller than 9, so 8 is added to the sol array and we move the pointer that had been pointing at 8 to the next element. However, at this point, we notice that there isn't another element. Our pointer is now pointing outside of the array, so we can't compare values. This does mean, however, that any remaining elements in the opposing array, in this case the red array, can be added to the end of the sol array.

![Merge Part ](http://i.imgur.com/klQQfJo.png)

9 is the only element left in the red array, so it is added to the sol array. The pointers are both pointing outside of their respective arrays, so we know that we are done merging our two arrays.
