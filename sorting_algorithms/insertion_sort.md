# Insertion Sort

Insertion sort is an improvement on selection sort. Insertion sort works on the premise that it should

![Insertion Sort Part 1](http://i.imgur.com/ak8yyOx.png)
Our pointer starts at the second element, 6.
![Insertion Sort Part 2](http://i.imgur.com/s7iS3OM.png)
Is 6 smaller than 3? It is not, so the pointer moves to the next element.
![Insertion Sort Part 3](http://i.imgur.com/0OIsSsq.png)
The pointer is now at the third element, 5.
![Insertion Sort Part 4](http://i.imgur.com/hV16Vjo.png)
Is 5 less than 6? It is, so 5 and 6 swap locations.
![Insertion Sort Part 5](http://i.imgur.com/ToLUCFT.png)
Is 5 less than 3? It is not, so the pointer moves to the next element.
![Insertion Sort Part 6](http://i.imgur.com/VdxfcVq.png)
The pointer is now at the fourth element, 4.
![Insertion Sort Part 7](http://i.imgur.com/cjwxa6i.png)
Is 4 less than 6? It is, so 4 and 6 swap locations.
![Insertion Sort Part 8](http://i.imgur.com/uwZBDFx.png)
Is 4 less than 5? It is, so 4 and 5 swap locations.
![Insertion Sort Part 9](http://i.imgur.com/NDj7EAD.png)
Is 4 less than 3? It is not, so the pointer moves to the next element.
![Insertion Sort Part 10](http://i.imgur.com/bUfNSep.png)
The pointer now points at the fifth element, 1.
![Insertion Sort Part 11](http://i.imgur.com/kpzV7HD.png)
Is 1 less than 6? It is, so 1 and 6 swap locations.
![Insertion Sort Part 12](http://i.imgur.com/xrlpLNO.png)
Is 1 less than 5? It is, so 1 and 5 swap locations.
![Insertion Sort Part 13](http://i.imgur.com/WHrE8f7.png)
Is 1 less than 4? It is, so 1 and 4 swap locations.
![Insertion Sort Part 14](http://i.imgur.com/n9HsPyQ.png)
Is 1 less than 3? It is, so 1 and 3 swap locations. 1 is now the first element, so the pointer moves to the next element.
![Insertion Sort Part 15](http://i.imgur.com/Y0UpBbl.png)
The pointer is now pointing at the 6th element, 2.
![Insertion Sort Part 16](http://i.imgur.com/9FblDXb.png)
Is 2 less than 6? It is, so 2 and 6 swap locations.
![Insertion Sort Part 17](http://i.imgur.com/nQFhHXE.png)
Is 2 less than 5? It is, so 2 and 5 swap locations.
![Insertion Sort Part 18](http://i.imgur.com/tnJIeVg.png)
Is 2 less than 4? It is, so 2 and 4 swap locations.
![Insertion Sort Part 19](http://i.imgur.com/f412kc9.png)
Is 2 less than 3? It is, so 2 and 3 swap locations.
![Insertion Sort Part 20](http://i.imgur.com/oFZ6O1z.png)
Is 2 less than 1? It is not. The pointer tries to move to the next element, but it is at the end of the array. The Insertion Sort algorithm exits.
![Insertion Sort Part 21](http://i.imgur.com/BjLDmRN.png)
The array is sorted!

## Almost Sorted Array

The insertion sort took a while to complete with the above array, but what happens if our array is almost already sorted? How long will it take to sort then?

![Almost Sorted Insertion Sort Part 1](http://i.imgur.com/USqiALL.png)
The array that is being sorted is almost already sorted.
![Almost Sorted Insertion Sort Part 2](http://i.imgur.com/7BvIx64.png)
The pointer starts at the second element. Is 2 smaller than 1? It is not, so the pointer goes to the next element.
![Almost Sorted Insertion Sort Part 3](http://i.imgur.com/TmPJih4.png)
Is 4 smaller than 2? It is not, so the pointer goes to the next element.
![Almost Sorted Insertion Sort Part 4](http://i.imgur.com/oxHIG8s.png)
Is 5 smaller than 4? It is not, so the pointer goes to the next element.
![Almost Sorted Insertion Sort Part 5](http://i.imgur.com/mxoi1HG.png)
Is 3 smaller than 5? It is, so 3 and 5 swap locations.
![Almost Sorted Insertion Sort Part 6](http://i.imgur.com/yKG7PLd.png)
Is 3 smaller than 4? It is, so 3 and 4 swap locations.

![Almost Sorted Insertion Sort Part 7](http://i.imgur.com/rGlhKQO.png)
Is 3 smaller than 2? It is not, so the pointer goes to the next element.

![Almost Sorted Insertion Sort Part 8](http://i.imgur.com/Od7X1AL.png)
Is 6 smaller than 5? It is not. The pointer is at the last element in the array, so the insertion sort exits.
![Almost Sorted Insertion Sort Part 9](http://i.imgur.com/BjLDmRN.png)
The array is sorted!

This was a lot faster to sort! Insertion sort is a bit smarter than selection sort. While selection sort has to check through each unsorted element when finding the next smallest number, insertion sort knows when to move on to the next element.
