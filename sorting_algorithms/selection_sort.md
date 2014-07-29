# Selection Sort

Selection sort was one of the first sorting algorithms invented and it is the first sorting algorithm we teach at MakerSquare.

![Sorting Array](http://i.imgur.com/PIKGhFq.png)

The array above is what we will be sorting using selection sort. The general idea behind selection sort is we are trying to find the smallest number in the array. Once we know where the smallest number is, we swap it with the first element in the array. Now we know that the first element is sorted, so we can move on to the next element. Let's take a look at what it looks like.

![Selection Sort Part ](http://i.imgur.com/4MLgtmQ.png)
We are switching out the first number in our array, 6, with the smallest number in the array. The place we are switching is marked yellow. The current smallest is marked red. The number we are comparing to the smallest is pointed to by the green arrow. We are comparing 3 with the first number, 6. Because 3 is smaller than 6, it is the current smallest number.

![Selection Sort Part ](http://i.imgur.com/oTQEnIO.png)
Our arrow continues moving through the array, one element at a time. We compare 5 to the smallest number, 3. 3 is still smaller than 5, so we do not change the smallest number.

![Selection Sort Part ](http://i.imgur.com/7Xa3gBk.png)
4 is not smaller than 3, so we continue on.

![Selection Sort Part ](http://i.imgur.com/jJb77be.png)
1 is smaller than 3, so we mark 1 as the smallest number.

![Selection Sort Part ](http://i.imgur.com/edYON3a.png)
2 is not smaller than 1. At this point we have reached the end of the array.

![Selection Sort Part ](http://i.imgur.com/B3fKeb9.png)
We now swap the smallest element, 1, with the first element in the array, 6.

![Selection Sort Part ](http://i.imgur.com/qFxTwGF.png)
Because 1 is the smallest element in the array and we are sorting from smallest to largest, we now know that 1 is in the correct position at the beginning of the array. 1 is now marked green to signify it is in the correct location.

![Selection Sort Part ](http://i.imgur.com/iPCwFpE.png)
We now start searching for the second smallest element in the array. We know that we are swapping the second element with the second smallest element in the array. 3 is smaller than 5, so we mark 3 as the smallest.

![Selection Sort Part ](http://i.imgur.com/yjrhZZT.png)
![Selection Sort Part ](http://i.imgur.com/8RLhaOL.png)
![Selection Sort Part ](http://i.imgur.com/QUKne9V.png)
Our algorithm continues through the rest of the array and finds that 2 is the second smallest element in the array.

![Selection Sort Part ](http://i.imgur.com/c4dExz4.png)
We swap 2 and 3.

![Selection Sort Part ](http://i.imgur.com/pJagWsN.png)
1 and 2 are now in their correct locations. We can continue working on the unsorted portion of the array.

![Selection Sort Part ](http://i.imgur.com/epmMOCU.png)
We are now swapping the third element (Currently containing 5) with the smallest remaining unsorted element in the array. We start with 5 and 4. 4 is smaller than 5, so it is marked as the smallest element.

![Selection Sort Part ](http://i.imgur.com/hy7H2aw.png)
4 is smaller than 6, so nothing changes.

![Selection Sort Part ](http://i.imgur.com/oag8F3L.png)
3 is smaller than 4, so we updated our smallest number to 3.

![Selection Sort Part ](http://i.imgur.com/O3eb0JS.png)
We now swap 5 and 3 to put 3 in its sorted place in our array.

![Selection Sort Part ](http://i.imgur.com/NaBW9UU.png)
1, 2, and 3 are in their sorted locations in the array.

![Selection Sort Part ](http://i.imgur.com/m0slScr.png)
The process continues with the remaining unsorted elements.

![Selection Sort Part ](http://i.imgur.com/xQ6i8I3.png)
![Selection Sort Part ](http://i.imgur.com/xEhvgvi.png)
![Selection Sort Part ](http://i.imgur.com/ZKzFBIm.png)
![Selection Sort Part ](http://i.imgur.com/jQo4rft.png)
![Selection Sort Part ](http://i.imgur.com/SZRs6KY.png)
Our array is sorted!
