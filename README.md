Download Link: https://assignmentchef.com/product/solved-cs3354-assignment-6
<br>
5/5 - (1 vote)

<span style="font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;">Goal:</span>

The goal of this assignment is to help students understand the concepts of Java Concurrency and Multi-threaded programming.

Description:The attached source code shows an example of a program that can sort a set of numbers using the top-down MergeSort1 algorithm. In the given implementation, the program uses a single thread to sort the whole input. MergeSort is a sorting algorithm that can be easily parallelized due its divide-and-conquer nature2. On CPUs with multiple cores, multiple threads can speed up the sorting time, by splitting the work.

MergeSort is a divide-and-conquer algorithm. It divides input array in two halves, calls itself for the two halves and then merges the two sorted halves. The merge() function is used for merging two halves. The merge(arr, l, m, r) is key process that assumes that arr[l..m] and arr[m+1..r] are sorted and merges the two sorted sub-arrays into one.

The figure below shows how an array of size 7 is split into two halves and it continues like that until each subarray is of size one, at which point it starts merging.

1 https://en.wikipedia.org/wiki/Merge_sort2 https://en.wikipedia.org/wiki/Merge_sort#Parallel_merge_sort

The following is a pseudocode of the MergeSort algorithm:

<pre>mergeSort(arr[], l,  r)if r &gt; l</pre>

<pre>    Find the middle point to divide the array into two halves:        middle m = (l+r)/2</pre>

<pre>    Call mergeSort for first half:        Call mergeSort(arr, l, m)</pre>

<pre>    Call mergeSort for second half:        Call mergeSort(arr, m+1, r)</pre>

<pre>parallelMergeSort(arr[], l,  r)if r &gt; l</pre>

<pre>    if (avalableTreads &lt;= 1)    elsemergeSort(arr[], l,  r) // Call original non-paralel mergeSort</pre>

<pre>        Find the middle point to divide the array into two halves:            middle m = (l+r)/2</pre>

<pre>        Call parallelMergeSort for first half in a new thread:            Call parallelMergeSort(arr, l, m) in new thread</pre>

<pre>        Call parallelMergeSort for second half in a new thread:            Call parallelMergeSort(arr, m+1, r) in new thread</pre>

<pre>        Wait for threads to finish</pre>

Tasks:

<pre>Merge the two halves sorted in step 2 and 3:    Call merge(arr, l, m, r)</pre>

The psedocode above can be modified to allow mergeSort(arr, l, m) and mergeSort(arr, m+1, r) to run in parallel.

<pre>Merge the two halves sorted in previous steps:    Call merge(arr, l, m, r)</pre>

Note that the pseudocode above uses the variable avalableTreads to decide whether to allocate a new thread or not based on the number of threads that has been made available to the program. That means that every time a new thread is created, the variable avalableTreads should be updated to reflect the number of threads that are still available.

1. Modify the MergeSorter class to convert it into a parallelized MergeSort that uses multiple threads to perform the sorting task. The maximum number of threads to be used should be passed as an argument to the sorting method. Your program should not allow more than the specified maximum number of threads to run in parallel. Call the modified class ParallelMergeSorter.

2. Modify the SortTester class provided to run some sorting simulations using the parallelized ParallelMergeSorter, to assess the possible speedup from using multiple threads, as opposed to a single thread. Call the modified class ParallelSortTester. Each experiment should time the sorting speed with different sizes of random number arrays, starting from an array of size 1000 and doubling the size of the array at each round, for 15 rounds (last round array size should be 16384000). Run the experiment with different number of threads starting from one thread and doubling the number of threads, up to the number of CPU cores available in your system. The number of cores available in your computer can be obtained from Java using the following statement Runtime.getRuntime().availableProcessors();.

Copy the output results and paste them into text file. Submit your output together with your code. At the end of this document you can see the output of an example run on my computer.

Notes:

1. For task 2 you will need to generate arrays with randomly distributed numbers (integers or doubles).

2. To make sure that your parallelized MergeSort works correctly, use the method isSorted, of the given class SortTester which takes an array as an input argument and returns true or false, depending on if the input array is sorted or not.

This assignment can be done and submitted individually by each student.Submit your answer in a single file (assign6_xxxxxx.zip). The xxxxxx is your TX State NetID.

Logistics:

Submit an electronic copy only, using the Assignments tool on the TRACS website for this class. Do NOT include executable or .class files in your submission.

Sample output of ParallelSortTester:

<pre>1 threads:      1000 elements  =&gt;</pre>

<pre>      2000 elements  =&gt;      4000 elements  =&gt;      8000 elements  =&gt;</pre>

<pre>     16000 elements  =&gt;     32000 elements  =&gt;     64000 elements  =&gt;</pre>

5 ms

6 ms 13 ms 26 ms

5 ms 10 ms 14 ms

<pre>    128000 elements  =&gt;    256000 elements  =&gt;    512000 elements  =&gt;</pre>

<pre>   1024000 elements  =&gt;   2048000 elements  =&gt;   4096000 elements  =&gt;   8192000 elements  =&gt;</pre>

<pre>  16384000 elements  =&gt;</pre>

<pre>2 threads:      1000 elements  =&gt;</pre>

<pre>      2000 elements  =&gt;      4000 elements  =&gt;      8000 elements  =&gt;</pre>

<pre>     16000 elements  =&gt;     32000 elements  =&gt;     64000 elements  =&gt;</pre>

<pre>    128000 elements  =&gt;    256000 elements  =&gt;    512000 elements  =&gt;</pre>

<pre>   1024000 elements  =&gt;   2048000 elements  =&gt;   4096000 elements  =&gt;   8192000 elements  =&gt;</pre>

<pre>  16384000 elements  =&gt;</pre>

<pre>4 threads:      1000 elements  =&gt;</pre>

<pre>      2000 elements  =&gt;      4000 elements  =&gt;      8000 elements  =&gt;</pre>

<pre>     16000 elements  =&gt;     32000 elements  =&gt;     64000 elements  =&gt;</pre>

<pre>    128000 elements  =&gt;    256000 elements  =&gt;    512000 elements  =&gt;</pre>

<pre>   1024000 elements  =&gt;   2048000 elements  =&gt;   4096000 elements  =&gt;   8192000 elements  =&gt;</pre>

<pre>  16384000 elements  =&gt;</pre>

<pre>8 threads:      1000 elements  =&gt;</pre>

<pre>      2000 elements  =&gt;      4000 elements  =&gt;</pre>

23 ms

<pre>  50 ms 107 ms 245 ms 541 ms</pre>

<pre>1243 ms2848 ms6425 ms</pre>

<pre>   1 ms   1 ms   1 ms   2 ms   4 ms   6 ms   7 ms</pre>

16 ms

<pre>  41 ms 105 ms 155 ms 360 ms 803 ms</pre>

<pre>1647 ms3474 ms</pre>

<pre>   1 ms   1 ms   1 ms   1 ms   3 ms   6 ms</pre>

<pre>  66 ms  12 ms  33 ms  54 ms</pre>

<pre> 131 ms 270 ms 690 ms</pre>

<pre>1119 ms3014 ms</pre>

1 ms

1 ms 64 ms

<pre>    8000 elements  =&gt;   16000 elements  =&gt;   32000 elements  =&gt;   64000 elements  =&gt;</pre>

<pre>  128000 elements  =&gt;  256000 elements  =&gt;  512000 elements  =&gt;</pre>

<pre> 1024000 elements  =&gt; 2048000 elements  =&gt; 4096000 elements  =&gt; 8192000 elements  =&gt;</pre>

<pre>16384000 elements  =&gt;</pre>

<pre>   1 ms   2 ms   3 ms   7 ms</pre>

<pre>  18 ms  22 ms  43 ms</pre>

<pre> 104 ms 250 ms 537 ms</pre>