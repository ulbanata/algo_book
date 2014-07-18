# Why Efficiency Matters

So with all of the talk about different Big Os, why does any of it matter? Aren't computers getting faster and faster? Yes, they are, but they're also able to store more and more data! And as your pc gets faster, people will want it to process more data. So what do the numbers look like? Let's take a look:

<table>
<tr>
<th>n</th>
<th>O(log(n))</th>
<th>O(n)</th>
<th>O(n*log(n))</th>
<th>O(n<sup>2</sup>)</th>
</tr>
<tr>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
<td>1</td>
</tr>
<tr>
<td>10</td>
<td>3.3</td>
<td>10</td>
<td>33.2</td>
<td>100</td>
</tr>
<tr>
<td>100</td>
<td>6.6</td>
<td>100</td>
<td>664.4</td>
<td>10,000</td>
</tr>
<tr>
<td>1,000</td>
<td>10.0</td>
<td>1,000</td>
<td>9,966</td>
<td>1,000,000</td>
</tr>
<tr>
<td>10,000</td>
<td>13.3</td>
<td>10,000</td>
<td>132,877</td>
<td>100,000,000</td>
</tr>
<tr>
<td>100,000</td>
<td>16.6</td>
<td>100,000</td>
<td>1,660,964</td>
<td>10,000,000,000</td>
</tr>
<tr>
<td>1,000,000</td>
<td>19.9</td>
<td>1,000,000</td>
<td>19,931,569</td>
<td>1,000,000,000,000</td>
</tr>
</table>

What we're looking at above is a table that shows the number of calculations that need to be done for different Big O algorithms. **n** shows the number of entries we are working with (such as elements in an array or number of nodes in a tree). The Big Os show the corresponding number of calculations needed to run the algorithm.

Wow, it looks like O(n<sup>2</sup>) takes a lot of time to run that algorithm! But how long does it really take? Let's use some time to find out. We'll say that each calculation takes 1 millisecond (1 ms) to run. Plugging that into our table results in the following amounts of time to finish each algorithm. Notice the units that are associated with each cell!

<table>
<tr>
<th>n</th>
<th>O(log(n))</th>
<th>O(n)</th>
<th>O(n*log(n))</th>
<th>O(n<sup>2</sup>)</th>
</tr>
<tr>
<td>1</td>
<td>1 ms</td>
<td>1 ms</td>
<td>1 ms</td>
<td>1 ms</td>
</tr>
<tr>
<td>10</td>
<td>3.3 ms</td>
<td>10 ms</td>
<td>33.2 ms</td>
<td>100 ms</td>
</tr>
<tr>
<td>100</td>
<td>6.6 ms</td>
<td>100 ms</td>
<td>664.4 ms</td>
<td>10 sec</td>
</tr>
<tr>
<td>1,000</td>
<td>10 ms</td>
<td>1 sec</td>
<td>10 sec</td>
<td>16.67 min</td>
</tr>
<tr>
<td>10,000</td>
<td>13.3 ms</td>
<td>10 sec</td>
<td>2.2 min</td>
<td>1.15 day</td>
</tr>
<tr>
<td>100,000</td>
<td>16.6 ms</td>
<td>1.67 min</td>
<td>27.7 min</td>
<td>3.8 month</td>
</tr>
<tr>
<td>1,000,000</td>
<td>19.9 ms</td>
<td>16.67 min</td>
<td>5.5 hour</td>
<td>31.7 years</td>
</tr>
</table>

Wow, look at the differences here. For 1 million entries, we can have an algorithm that takes anywhere from 19.9 milliseconds to 31.7 years, depending on how efficient it is. This is why the efficiency matters. Use the wrong algorithm for a large data set and it could take a long time to finish. Do this on a website and you'll cause it to crash. Cause your website to crash and your company can lose a lot of money from lack of sales during the downtime or upset customers ending their contracts. It has happened before and it will happen again. The purpose of this book is to get you to think about how your algorithm works and how to improve them so that won't happen to you!

(For a little more context, 1,000,000 entries being ran through a factorial algorithm will have a run time that is longer than the expected lifespan of the universe)

**NOTE** The times above are completely arbitrary to show why efficiency matters. Most calculations will not take exactly 1 millisecond to run and can fluctuate. Don't use the above as the absolute truth on runtimes! It is just a demonstration.
