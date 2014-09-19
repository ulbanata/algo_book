# Radix Sort

### Non-stable and Non-adaptive - O(n)

Radix sort is a very efficient sort in some specific cases. For some cases, it can sort in O(n) time! The sorts we had been working with were **comparison sorts**; they sorted the elements in the array by comparing them to one another. Radix sort is a non-comparison sorting algorithm. It only works for integers, but it can be extremely efficient when you know the number of digits in the integers you might be receiving.

Radix sort works by looking at each number one digit at a time. Depending on what the digit is, it is placed into a **bucket**, or container, corresponding to the number.

## Sort Visualization

Below is the array we will be sorting, along with the buckets we will be storing the numbers in.

![Radix Sort Part ](http://i.imgur.com/fPFdqlW.png)

### The Ones Sort

We start by putting each number in the array into its correct buckets based on the number in its ones place. For 63, the number in its ones place is 3. This means that 63 goes in the 3 bucket.

![Radix Sort Part ](http://i.imgur.com/ulW2KZZ.png)

901's ones number is 1, so it goes in bucket 1.

![Radix Sort Part ](http://i.imgur.com/gZMoPiG.png)

634 goes in bucket 4, because its ones number is 4.

![Radix Sort Part ](http://i.imgur.com/0iEJkXi.png)

7 goes in bucket 7.

![Radix Sort Part ](http://i.imgur.com/Ogsi2bc.png)

297 goes in bucket 7.

![Radix Sort Part ](http://i.imgur.com/asaMQhk.png)

219 goes in bucket 9.

![Radix Sort Part ](http://i.imgur.com/aPp1jug.png)

Now that all numbers are in buckets, we need to extract them back into an array. To do this, we start with bucket 0 and empty it from the bottom. When a bucket is empty, we move to the next bucket and repeat the emptying process.

![Radix Sort Part ](http://i.imgur.com/ks2yrWB.png)

Bucket 0 is empty, so we start with bucket 1. 901 is the number in bucket 1, so we remove it from the bucket and push it to the new array.

![Radix Sort Part ](http://i.imgur.com/V0IP29d.png)

The next non-empty bucket is bucket 2. We remove 432 from bucket 2 and push it to the new array.

![Radix Sort Part ](http://i.imgur.com/1X2iwxe.png)

Next is bucket 3, which contains 63. 63 gets pushed to the new array.

![Radix Sort Part ](http://i.imgur.com/dKjDlMS.png)

634 is removed from bucket 4 and is pushed to the new array.

![Radix Sort Part ](http://i.imgur.com/KvCltD3.png)

Bucket 7 is an interesting case. It has two numbers in it. In order to ensure that the sort does sort the numbers, we need to remove the numbers from the bottom of the bucket first. This makes each bucket act like a queue. If we take from the bottom of the bucket, then 7 gets removed from bucket 7 and pushed to the new array.

![Radix Sort Part ](http://i.imgur.com/pRBbfmC.png)

Then 297 gets removed from bucket 7 and pushed into the new array.

![Radix Sort Part ](http://i.imgur.com/SVJFtKu.png)

Finally, 219 is removed from bucket 9 and pushed to the new array.

### The 10s Sort

![Radix Sort Part ](http://i.imgur.com/KBXxfU8.png)

At this point, we've got an array of all of our elements. At first look, it looks like we haven't really done anything. The elements are still in an unsorted order. 901, which should be at the end of the array, is at the beginning! However, we are making progress! We need to repeat the process, but this time sort each number by the number in their 10s place.

![Radix Sort Part ](http://i.imgur.com/hYHv1wK.png)

We start with 901. 0 is the number in 901's 10s place, so 901 goes into bucket 0.

![Radix Sort Part ](http://i.imgur.com/7UPzrKo.png)

432's has a 3 in its 10s place. We place 432 into bucket 3. We repeat this pattern until we have added each element to a bucket.

![Radix Sort Part ](http://i.imgur.com/EfMhZ6Y.png)
![Radix Sort Part ](http://i.imgur.com/hpN6A4T.png)
![Radix Sort Part ](http://i.imgur.com/CR96BTV.png)

Note that for 7, its 10s place is the number 0. 7 could also be written 07, but we ignore the 0 when writing the number. Because of this, 7 goes into bucket 0.

![Radix Sort Part ](http://i.imgur.com/IOzluzt.png)
![Radix Sort Part ](http://i.imgur.com/Y7gFnWl.png)

We have all of the numbers in our array sorted into buckets based off of the number in their 10s place. It's time to extract them from the buckets.

![Radix Sort Part ](http://i.imgur.com/F1lsHTD.png)

Bucket 0 is emptied from the bottom, so we remove 901 from the bucket first and push it to the new array.

![Radix Sort Part ](http://i.imgur.com/SuIqUDW.png)

We then remove 7 from bucket 0 and push it to the new array. This process repeats until the buckets are empty.

![Radix Sort Part ](http://i.imgur.com/9sKevF3.png)
![Radix Sort Part ](http://i.imgur.com/eO5ZL7x.png)
![Radix Sort Part ](http://i.imgur.com/yiVvvoC.png)
![Radix Sort Part ](http://i.imgur.com/IViwc2l.png)

### The 100s Sort

![Radix Sort Part ](http://i.imgur.com/AGZsWkH.png)

At this point, we have an array that still looks completely unsorted. There seems to be no semblance of order in our array. It seems like we've done nothing at all! But, with just one more pass through, we'll have completely sorted this array. We need to run through one more time, sorting by the 100s spot.

![Radix Sort Part ](http://i.imgur.com/oJ3Auyb.png)

901 has a 9 in its 100s place, so 901 goes to bucket 9.

![Radix Sort Part ](http://i.imgur.com/S1KGvFc.png)

7 has a 0 in its 100s place, because 7 can also be written as 007, and goes into bucket 0. This process is repeated until every element in the array is assigned to a bucket.

![Radix Sort Part ](http://i.imgur.com/k1c8C4z.png)
![Radix Sort Part ](http://i.imgur.com/zNfeBZT.png)
![Radix Sort Part ](http://i.imgur.com/uRIpRFj.png)
![Radix Sort Part ](http://i.imgur.com/gcyQDdx.png)
![Radix Sort Part ](http://i.imgur.com/4FH07nX.png)

All of the elements in the array have been assigned to buckets. If you take a look at the buckets, you can see that everything now appears to be sorted. When we start emptying the buckets, they will assemble a sorted array.

![Radix Sort Part ](http://i.imgur.com/LFQDGj6.png)

7 is removed from the bottom bucket 0 and is pushed to the new array.

![Radix Sort Part ](http://i.imgur.com/x0e1CQi.png)

63 is then removed from bucket 0 and pushed to the new array. This continues until the buckets are empty.

![Radix Sort Part ](http://i.imgur.com/Z0e2cLy.png)
![Radix Sort Part ](http://i.imgur.com/uoblD64.png)
![Radix Sort Part ](http://i.imgur.com/xdnDb8l.png)
![Radix Sort Part ](http://i.imgur.com/LRBQy5U.png)
![Radix Sort Part ](http://i.imgur.com/Whl4sHT.png)

Finally! We have a sorted array! But did this really save any time? What was the run time in this particular case? Well, every time we sorted the elements into the buckets, we had to touch each element once. So it is `O(n)` to move elements to the buckets. How many times did we have to sort into the buckets? For this array, it was 3 times. The number will always be the number of digits that exist in the largest number. For this array, the max number was 901, and it had 3 digits. So, the overall runtime was `O(3n)`, which can be reduced down to `O(n)`.

## Challenge:

Write out a method that implements radix sort for an array of numbers. It should be able to take any array of numbers and sort it, not just numbers that are # of digits long.
