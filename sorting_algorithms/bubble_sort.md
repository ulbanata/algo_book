# Bubble Sort

Bubble sort is another adaptive sorting algorithm that is an improvement on selection sort. Bubble sort starts at the end of the array and moves the smallest element into its correct location pass at a a time by swapping elements if they are smaller than the preceding element. The algorithm also keeps track of the last element it swapped to determine when it can skip that group of elements.

![Bubble Sort Part ](http://i.imgur.com/vEii5qt.png)
The algorithm starts at the end of the array. It compares the last element and the next to last element and swaps them if the last element is less than the next to last element. Is 2 smaller than 1? It is not, so it checks the next two elements.

![Bubble Sort Part ](http://i.imgur.com/pFyU9Cd.png)
Is 1 smaller than 4? It is, so their locations are swapped.

![Bubble Sort Part ](http://i.imgur.com/TTAX1Sn.png)
Is 1 smaller than 5? It is, so their locations are swapped.

![Bubble Sort Part ](http://i.imgur.com/GG4m4ZY.png)
Is 1 smaller than 3? It is, so their locations are swapped.

![Bubble Sort Part ](http://i.imgur.com/HNZNJa6.png)
Is 1 smaller than 6? It is, so their locations are swapped.

![Bubble Sort Part ](http://i.imgur.com/U1fW2zQ.png)
The algorithm has reached the beginning of the array. At this point in time, we know that the smallest element is in its correct location. The algorithm starts again from the last element and compares it to the next to last element.

Is 2 less than 4? It is, so their locations are swapped.

![Bubble Sort Part ](http://i.imgur.com/jXslI9W.png)
Is 2 less than 5? It is, so their locations are swapped.

![Bubble Sort Part ](http://i.imgur.com/Bdf6wkX.png)
Is 2 less than 3? It is, so their locations are swapped.

![Bubble Sort Part ](http://i.imgur.com/LQcp0Ba.png)
Is 2 less than 6? It is, so their locations are swapped.

![Bubble Sort Part ](http://i.imgur.com/GVD0z2h.png)
The algorithm has reached the pointer that lets us know we have reached an element that has been sorted. We now know that 2 is in its correct spot in the array. The algorithm starts from the last elements and compares it to the next to last element.

Is 4 less than 5? It is, so their locations are swapped.

![Bubble Sort Part ](http://i.imgur.com/qexQ6ht.png)

Is 4 less than 3? It is not.

![Bubble Sort Part ](http://i.imgur.com/eEmzU2W.png)

Is 3 less than 6? It is, so their locations are swapped.

![Bubble Sort Part ](http://i.imgur.com/7Ch1kWR.png)

The algorithm has once again reached the pointer. It knows that the element 3 is in its correct sorted location. The algorithm repeats to finish sorting the array.

![Bubble Sort Part ](http://i.imgur.com/6FNOOHX.png)
![Bubble Sort Part ](http://i.imgur.com/dVi4IYG.png)
![Bubble Sort Part ](http://i.imgur.com/Uo3FNWp.png)

The array has been sorted!

## Almost Sorted Array

Just like with insertion sort, bubble sort is adapative, which means that it is more efficient with almost sorted arrays. Let's see what that looks like.

![Almost Sorted Bubble Sort Part ](http://i.imgur.com/USqiALL.png)

Here is our almost sorted array.

![Almost Sorted Bubble Sort Part ](http://i.imgur.com/1CePv6q.png)

Is 6 less than 3? It is not, so nothing is swapped.

![Almost Sorted Bubble Sort Part ](http://i.imgur.com/srTzv0C.png)

Is 3 less than 5? It is, so the locations are swapped.

![Almost Sorted Bubble Sort Part ](http://i.imgur.com/bdoMHoj.png)

Is 3 less than 4? It is, so the locations are swapped.

![Almost Sorted Bubble Sort Part ](http://i.imgur.com/eAmzAYZ.png)

Is 3 less than 2? It is not, so nothing is swapped.

![Almost Sorted Bubble Sort Part](http://i.imgur.com/0mO7Kxu.png)

Is 2 less than 1? It is not, so nothing is swapped. The algorithm reached the beginning of the array, so the sorted elements are calculated and the pointer is assigned.

![Almost Sorted Bubble Sort Part ](http://i.imgur.com/YCQcxW1.png)

At this point, we know that elements 1, 2, and 3 are in their correnct locations. This is because the last swap occurred when we swapped 3 and 4's locations. The algorithm restarts at the end of the array.

Is 6 less than 4? It is not, so nothing is swapped.

![Almost Sorted Bubble Sort Part ](http://i.imgur.com/9QU7AAC.png)

It 4 less than 5? It is, so the locations are swapped.

![Almost Sorted Bubble Sort Part ](http://i.imgur.com/qIoaAkK.png)

We now know that 1, 2, 3, and 4 are in the correct, sorted locations. The algorithm continues to determine if the last two elements are in the correct location.

![Almost Sorted Bubble Sort Part ](http://i.imgur.com/Uo3FNWp.png)

The array is sorted!
