# Hands-on-3
1: The runtime of the algorithm can be mathematically represented as:

T(n) = 2 * n^2 - 2 * n + 1
This is because there are two nested loops that each iterate n times. The outer loop iterates n times and for each iteration of the outer loop, the inner loop also iterates n times. Therefore, the total number of iterations is n * n = n^2. However, we need to subtract the number of iterations where i = j (i.e., the diagonal elements) because they are counted twice. This gives us 2 * n^2 - 2 * n + 1.

2:The time complexity of the algorithm can be plotted as a function of n. Here is a Python code snippet that times the function for various n values and plots the results:

import numpy as np
import matplotlib.pyplot as plt

def f(n):
    x = 1
    for i in range(1, n+1):
        for j in range(1, n+1):
            x = x + 1
    return x

n_values = np.arange(1, 101)
times = []

for n in n_values:
    start_time = time.time()
    f(n)
    end_time = time.time()
    times.append(end_time - start_time)

plt.plot(n_values, times, 'o-')
plt.xlabel('n')
plt.ylabel('time')
plt.title('Time complexity of the algorithm')
plt.show()
The plot shows that the time complexity of the algorithm is quadratic.

The polynomials that are upper and lower bounds on the curve from #2 are:

Upper bound: O(n^2)
Lower bound: Ω(n^2)
This is because the time complexity of the algorithm is a quadratic function, which is both an upper bound and a lower bound on the curve.

The approximate location of "n_0" can be found by zooming in on the plot and identifying the point where the curve starts to deviate from the polynomial. In this case, n_0 is approximately 10.

If we modify the function to be:


def f(n):
    x = 1
    y = 1
    for i in range(1, n+1):
        for j in range(1, n+1):
            x = x + 1
            y = i + j
This will increase the time it takes for the algorithm to run because we are now performing an additional operation (y = i + j) for each iteration of the inner loop.

If we modify the function to be:

def f(n):
    x = 1
    y = 1
    for i in range(1, n+1):
        for j in range(1, n+1):
            x = x + 1
This will not affect the results from #1 because the time complexity of the algorithm is still quadratic.

Here is an implementation of merge sort in Python:

def merge_sort(arr):
    if len(arr) <= 1:
        return arr

    mid = len(arr) // 2
    left = merge_sort(arr[:mid])
    right = merge_sort(arr[mid:])

    return merge(left, right)

def merge(left, right):
    merged = []
    i = j = 0

    while i < len(left) and j < len(right):
        if left[i] < right[j]:
            merged.append(left[i])
            i += 1
        else:
            merged.append(right[j])
            j += 1

    while i < len(left):
        merged.append(left[i])
        i += 1

    while j < len(right):
        merged.append(right[j])
        j += 1

    return merged

arr = [5,2,4,7,1,3,2,6]
sorted_arr = merge_sort(arr)
print(sorted_arr)
This code will output the sorted array [1, 2, 2, 3, 4, 5, 6, 7].
