Hands-On 3: Questions 1 - 6

1.The algorithm has two nested for loops, with the outer loop iterating from 1 to n, and the inner loop iterating from 1 to n.

Outer loop iterations:
∑i = 1 to n

Inner loop iterations per outer iteration:
∑j = 1 to n

So the total number of inner loop iterations is:
∑i = 1 to n ( ∑j = 1 to n )

Expanding this:
∑i = 1 to n ( ∑j = 1 to n )
= n * n
= n^2

Inside the inner loop is the statement:
x = x + 1

This takes constant time c.

Therefore, the total runtime is:

T(n) = n^2 * c
= O(n^2)

So in summary, the mathematical runtime analysis shows this algorithm has a time complexity of O(n^2) due to the nested loops iterating n times each.
    The runtime would be calculated with the following summation formula:
    <br />
    $$T(n) = 1 + \sum_{i=1}^{n+1} 1 + \sum_{i=1}^{n} \sum_{j=1}^{n+1} 1 + \sum_{i=1}^{n} \sum_{j=1}^{n} 1$$
    $$\Rightarrow T(n) = 1 + (n+1) + n(n+1) + n^2$$
    $$\Rightarrow T(n) = 2n^2 + 2n + 2$$
2. Calculations table:
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
    For graph open(graph-1.png)

3. The polynomials that are upper and lower bounds on the curve from #2 are:
Upper bound: O(n^2)
Lower bound: Ω(n^2)
This is because the time complexity of the algorithm is a quadratic function, which is both an upper bound and a lower bound on the curve.

4.The approximate location of "n_0" can be found by zooming in on the plot and identifying the point where the curve starts to deviate from the polynomial. In this case, n_0 is approximately 10.
   For graph open(Graph-2.png)
    As shown in the figure above, at x=1.4 the upper bound is larger than T(n), therefore, n_0=2 is the first integer that T(n) respects both bounds

5. In case the function changed as stated in the question: 
    def f(n):
    x = 1
    y = 1
    for i in range(1, n+1):
        for j in range(1, n+1):
            x = x + 1
   This will not affect the results from #1 because the time complexity of the algorithm is still quadratic.
6. The results change as follows:
    
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


