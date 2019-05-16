---
title: Assignment 1
author: Derek Sifford
date: 2015/05/15
---

## Exercises 1.1 (2 points)

### Problem 5

> Design an algorithm to ﬁnd all the common elements in two sorted lists of
> numbers. For example, for the lists 2, 5, 5, 5 and 2, 2, 3, 5, 5, 7, the
> output should be 2, 5, 5. What is the maximum number of comparisons your
> algorithm makes if the lengths of the two given lists are _m_ and _n_,
> respectively?

## Exercises 1.2 (4 points)

### Problem 5

> Describe the standard algorithm for ﬁnding the binary representation of a
> positive decimal integer a). in English. and b). in pseudocode.

## Exercises 1.3 (3 points)

### Problem 1

> Consider the algorithm for the sorting problem that sorts an array by
> counting, for each of its elements, the number of smaller elements and then
> uses this information to put the element in its appropriate position in the
> sorted array:

```
ALGORITHM ComparisonCountingSort(A[0..n − 1])
    // Sorts an array by comparison counting
    // Input: Array A[0..n − 1] of orderable values
    // Output: Array S[0..n − 1] of A’s elements sorted in nondecreasing order
    for i ← 0 to n − 1 do
        Count[i] ← 0
    for i ← 0 to n − 2 do
        for j ← i + 1 to n − 1 do
            if A[i] < A[j ]
                Count[j ] ← Count[j ] + 1
            else Count[i] ← Count[i] + 1
    for i ← 0 to n − 1 do
        S[Count[i]] ← A[i]
    return S
```

> a. Apply this algorithm to sorting the list 60, 35, 81, 98, 14, 47.

> b. Is this algorithm stable?

> c. Is it in-place?

## Exercises 1.4 (7 points)

### Problem 2

> If you have to solve the searching problem for a list of n numbers, how can
> you take advantage of the fact that the list is known to be sorted? Give
> separate answers for...

> a. lists represented as arrays.

> b. lists represented as linked lists.

### Problem 4 (3 points)

> a. Let A be the adjacency matrix of an undirected graph. Explain what property
> of the matrix indicates that...

> i. the graph is complete.

> ii. the graph has a loop, i.e., an edge connecting a vertex to itself.

> iii. the graph has an isolated vertex, i.e., a vertex with no edges incident
> to it.

> b. Answer the same questions for the adjacency list representation.

### Problem 10

> Design an algorithm for checking whether two given words are anagrams, i.e.,
> whether one word can be obtained by permuting the letters of the other. For
> example, the words _tea_ and _eat_ are anagrams.

## Exercises 2.1: (6 points)

### Problem 8

> For each of the following functions, indicate how much the function’s value
> will change if its argument is increased fourfold.

a. $log_2 n$

b. $\sqrt{n}$

c. $n$

d. $n^2$

e. $n^3$

f. $2^n$

### Problem 9

> For each of the following pairs of functions, indicate whether the ﬁrst
> function of each of the following pairs has a lower, same, or higher order of
> growth (to within a constant multiple) than the second function.

a. $n(n + 1)$ and $2000n^2$

b. $100n^2$ and $0.01n^3$

c. $\log_2 n$ and $\ln{n}$

d. $\log_2^2 n$ and $\log_2 n^2$

e. $2^{n−1}$ and $2^n$

f. $(n − 1)!$ and $n!$

## Exercises 2.2 (8 points)

### Problem 3 (part a,b,d,& e) (4 points)

> For each of the following functions, indicate the class $\Theta(g(n))$ the
> function belongs to. (Use the simplest g(n) possible in your answers.) Prove
> your assertions.

a. $(n^2 + 1)^{10}$

b. $\sqrt{10n^2 + 7n + 3}$

d. $2^{n+1} + 3^{n-1}$

e. $\lfloor \log_2 n \rfloor$

### Problem 5

> List the following functions according to their order of growth from the
> lowest to the highest:

$(n-2)!$, $5\lg(n+100)^{10}$, $2^{2n}$, $0.001n^4 + 3n^3 + 1$, $\ln^2 n$,
$\sqrt[3]{n}$, $3^n$

### Problem 10

> The range of a ﬁnite nonempty set of $n$ real numbers $S$ is deﬁned as the
> difference between the largest and smallest elements of $S$. For each
> representation of $S$ given below, describe in English an algorithm to compute
> the range. Indicate the time efﬁciency classes of these algorithms using the
> most appropriate notation ($O$, $\Theta$, or $\Omega$).

> a. An unsorted array

> b. A sorted array

> c. A sorted singly linked list

> d. A binary search tree

## Exercises 2.3 (4 points)

### Problem 2

> Find the order of growth of the following sums. Use the $\Theta(g(n))$
> notation with the simplest $g(n)$ possible.

> a. $\sum_{i=1}^{n-1}(i^2 + 1)^2$

> b. $\sum_{i=2}^{n-1}\lg i^2$

> c. $\sum_{i=1}^n(i+1)2^{i-1}$

> d. $\sum_{i=0}^{n-1}\sum_{j=0}^{i-1}(i+j)$

### Problem 5

> Consider the following algorithm...

```
ALGORITHM Secret(A[0..n − 1])
    // Input: An array A[0..n − 1] of n real numbers
    minval ← A[0];
    maxval ← A[0]
    for i ← 1 to n − 1 do
        if A[i] < minval
            minval ← A[i]
        if A[i] > maxval
            maxval ← A[i]
    return maxval − minval
```

> a. What does this algorithm compute?

> b. What is its basic operation?

> c. How many times is the basic operation executed?

> d. What is the efﬁciency class of this algorithm?

> e. Suggest an improvement, or a better algorithm altogether, and indicate its
> efﬁciency class. If you cannot do it, try to prove that, in fact, it cannot be
> done.

## Exercises 2.4 (6 points)

### Problem 1(a,b,c)

> Solve the following recurrence relations...

> a. $x(n) = x(n - 1) + 5$ for $n > 1$, $x(1) = 0$

> b. $x(n) = 3x(n - 1)$ for $n > 1$, $x(1) = 4$

> c. $x(n) = x(n - 1) + n$ for $n > 0$, $x(0) = 0$

### Problem 4

> Consider the following recursive algorithm...

```
ALGORITHM Q(n)
    // Input: A positive integer n
    if n = 1 return 1
    else return Q(n − 1) + 2 * n − 1
```

> a. Set up a recurrence relation for this function’s values and solve it to
> determine what this algorithm computes.

> b. Set up a recurrence relation for the number of multiplications made by this
> algorithm and solve it.

> c. Set up a recurrence relation for the number of additions/subtractions made
> by this algorithm and solve it.
