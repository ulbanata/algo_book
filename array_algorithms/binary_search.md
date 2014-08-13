# Binary Search

The `.include?` method runs in O(n) time. Is there a faster way to search through an array? There is, but it comes with a caveat. If the array is sorted already, you can find out if an object is in it in O(log(n)) time instead of O(n)!

The power of binary search comes from the fact that the array is sorted. Because of this, we know that if the element we are looking at in the array is smaller than what we are looking for, then all elements to the left, including the element we are looking at, don't contain our search term. That means that if we start searching from the middle, we can ignore half the array at a time! This process should be similar to the split in merge sort, where we saw that we can split up an array into individual elements in O(log(n)) time.

Let's run through a binary search for an array. We will search for the number 4.

![Binary Search Part 1](http://i.imgur.com/x2Aa1Og.png)
We're going to go through the below sorted array and apply a binary search on it to determine if the number 4 is in it.

![Binary Search Part 2](http://i.imgur.com/c7N1AXR.png)
First we start at the midpoint of the array. Because it is an even number array, we'll start at index 4. Here we see if the midpoint is equal to the number we're looking for. 9 is not equal to 4, but 9 is larger than 4. Because the array is sorted, we know that all numbers to the right in the array are not 4, so we can ignore them and only focus on the left side of the array.

![Binary Search Part 3](http://i.imgur.com/FSbfysY.png)
We now have only the left side of the array to consider. Let's find the midpoint of this new portion of the array.

![Binary Search Part 4](http://i.imgur.com/K7lTjSq.png)
The midpoint is 5. We check to see if 5 is equal to 4. It is not, but 5 is greater than 4, so we can ignore all numbers right of 5.

![Binary Search Part 5](http://i.imgur.com/RRIApyi.png)
Now we only have 2 elements to search through. We'll grab the midpoint again.

![Binary Search Part 6](http://i.imgur.com/CqjVZCx.png)
Our midpoint is now 4. We check to see if the midpoint points to what we're searching for. 4 equals 4, so the binary search returns true.

The astutue observer will notice that the 3 steps we took is actually slower than if we had used the `.include?` method (which would take 2 steps for searching for the number 4). What happens if we search for an element that doesn't exist in the array? How many steps will it take?

To find out, we'll search for the number 14, which is not present in the array.

![Binary Search Part 1](http://i.imgur.com/x2Aa1Og.png)
We'll go through the binary search again, but this time we'll search for 14.

![Binary Search Part 2](http://i.imgur.com/c7N1AXR.png)
We start at the midpoint again. 9 does not equal 14, but 9 is less than 14. We can ignore the left half of the array.

![Binary Search Part 3](http://i.imgur.com/DsHkMqE.png)
We now only have 3 elements to work through. Time to find the midpoint.

![Binary Search Part 4](http://i.imgur.com/A6L9UWq.png)
The midpoint points to 15. 15 does not equal 14, but 15 is greater than 14. We can ignore the right portion of the small array.

![Binary Search Part 5](http://i.imgur.com/BAOCJFy.png)
Only 1 element remaining!

![Binary Search Part 6](http://i.imgur.com/7O0t5Kl.png)
The midpoint of a 1 element array is that single element. We check to see if 12 is equal to 14, and it is not. 12 is smaller than 14, so we can ignore all of the elements to the left of 12.

![Binary Search Part 7](http://i.imgur.com/ZXQdljl.png)
There are no more possible elements that contain the number 14, so the binary search returns false.

It took a total of 3 steps to decide that the number 14 is not in our array! This is much faster than the 8 steps it would have normally taken for the `.include?` method.

# Coding Challenge

Implement binary search so that it can take any sorted array of numbers and see if a number is present in the array. Write both a recursive and an iterative solution.
