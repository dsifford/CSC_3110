---
title: Assignment 1
author: Derek Sifford
date: 2015/05/15
---

## Exercises 1.1 (2 points)

### 1. Problem 5

> Design an algorithm to ﬁnd all the common elements in two sorted lists of
> numbers. For example, for the lists 2, 5, 5, 5 and 2, 2, 3, 5, 5, 7, the
> output should be 2, 5, 5. What is the maximum number of comparisons your
> algorithm makes if the lengths of the two given lists are _m_ and _n_,
> respectively?

```
ALGORITHM CommonElements(a[0..n-1], b[0..m-1], commons = [])
    if length(a) == 0 OR length(b) == 0
        return commons
    if a[0] < b[0]
        return CommonElements(a[1..], b, commons)
    if a[0] > b[0]
        return CommonElements(a, b[1..], commons)
    i ← a[0]
    return CommonElements(a[1..], b[1..], [...commons, i])
```

The maximum number of comparisons (iterations) that this recursive algorithm
makes given two lists of lengths $n$ and $m$ is $n$ if $n > m$ or $m$ if
$m > n$. In other words, this algorithm will iterate the total length of the
longer list (worst case).

## Exercises 1.2 (4 points)

### 2. Problem 5

> Describe the standard algorithm for ﬁnding the binary representation of a
> positive decimal integer a). in English. and b). in pseudocode.

#### Steps in English

1. Take the integer and divide it by 2.
2. Prepend the remainder of that division to a string used for the binary
   represenatation.
3. If the result is greater than zero, repeat from step 1 with the result.
4. Otherwise, return the binary string.

#### Pseudocode

```
ALGORITHM DecimalToBinary(n, result = '')
    if n == 0
        return result
    return DecimalToBinary(floor(n / 2), (n mod 2) + result)
```

## Exercises 1.3 (3 points)

### 3. Problem 1

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
            if A[i] < A[j]
                Count[j] ← Count[j] + 1
            else Count[i] ← Count[i] + 1
    for i ← 0 to n − 1 do
        S[Count[i]] ← A[i]
    return S
```

> a. Apply this algorithm to sorting the list 60, 35, 81, 98, 14, 47.

|   i |  60 |  35 |  81 |  98 |  14 |  47 |
| --: | --: | --: | --: | --: | --: | --: |
|   0 |   3 |   0 |   1 |   1 |   0 |   0 |
|   1 |     |   1 |   2 |   2 |   0 |   1 |
|   2 |     |     |   4 |   3 |   0 |   1 |
|   3 |     |     |     |   5 |   0 |   1 |
|   4 |     |     |     |     |   0 |   2 |

**Final State:** `[3, 1, 4, 5, 0, 2]`

> b. Is this algorithm stable?

No, the algorithm is not stable.

> c. Is it in-place?

No, the sorting is not in-place.

## Exercises 1.4 (7 points)

### 4. Problem 2

> If you have to solve the searching problem for a list of n numbers, how can
> you take advantage of the fact that the list is known to be sorted? Give
> separate answers for...

> a. lists represented as arrays.

This is the ideal case. If we're using an indexed array of a known length, we
can simply perform a binary search to find the item of interest.

> b. lists represented as linked lists.

This is less ideal than above, due to the fact that we would still need to
sequentially move from the front of the list to the item. However, having a
known sorted array is helpful here because the moment we encounter an item
larger than the item of interest, we know for sure that it does not exist in the
list and we can stop, rather than having to iterate the entire list for it.

### 5. Problem 4 (3 points)

#### Part a)

> Let $A$ be the **adjacency matrix** of an undirected graph. Explain what
> property of the matrix indicates that...

> i. the graph is complete.

The graph is complete if all of its elements are `1` _except_ the elements in
the main diagonal.

> ii. the graph has a loop, i.e., an edge connecting a vertex to itself.

The graph has a loop if any of its elements in the main diagonal are `1`.

> iii. the graph has an isolated vertex, i.e., a vertex with no edges incident
> to it.

The graph has an isolated vertex if any row contains all `0`s.

#### Part b)

> Answer the same questions for the adjacency list representation. Let $A$ be
> the **adjacency list** of an undirected graph. Explain what property of the
> list indicates that...

> i. the graph is complete.

The graph is complete if **all** of the lists contain **all** of the other
items.

> ii. the graph has a loop, i.e., an edge connecting a vertex to itself.

The graph has a loop if **any** of the lists contain a reference to the itself.

> iii. the graph has an isolated vertex, i.e., a vertex with no edges incident
> to it.

The graph has an isolated vertex if **any** of the lists are empty.

### 6. Problem 10

> Design an algorithm for checking whether two given words are anagrams, i.e.,
> whether one word can be obtained by permuting the letters of the other. For
> example, the words _tea_ and _eat_ are anagrams.

```
ALGORITHM AreAnagrams(a[0..n], b[0..m])
    // Input(a): character list of word 1
    // Input(b): character list of word 2
    // Output: true if words are anagrams, false otherwise
    if n == 0 AND m == 0
        return true
    if n == 0 OR m == 0
        return false
    letter ← a[0]
    for i ← 0 to m do
        if b[i] == letter
            // remove letter from b
            b ← b[0..i] + b[i+1..]
            break
    return AreAnagrams(a[1..], b)
```

## Exercises 2.1: (6 points)

### 7. Problem 8

> For each of the following functions, indicate how much the function’s value
> will change if its argument is increased fourfold.

> a. $\log_2 n$

$$
\log_2 4n = \log_2 n = (\log_2 4 + \log_2 n) - \log_2 n = 2
$$

> b. $\sqrt{n}$

$$
\frac{\sqrt{4n}}{\sqrt{n}} = 2 \frac{\sqrt{n}}{\sqrt{n}} = 2
$$

> c. $n$

$$
\frac{4n}{n} = 4
$$

> d. $n^2$

$$
\frac{4n^2}{n^2} = 16
$$

> e. $n^3$

$$
\frac{4n^3}{n^3} = 64
$$

> f. $2^n$

$$
\frac{2^{4n}}{2^n} = 2^{4n - n} = 2^{3n} = (2^n)^3
$$

### 8. Problem 9

> For each of the following pairs of functions, indicate whether the ﬁrst
> function of each of the following pairs has a lower, same, or higher order of
> growth (to within a constant multiple) than the second function.

> a. $n(n + 1)$ and $2000n^2$

Same

> b. $100n^2$ and $0.01n^3$

Lower

> c. $\log_2 n$ and $\ln{n}$

Same

> d. $\log_2^2 n$ and $\log_2 n^2$

Higher

> e. $2^{n−1}$ and $2^n$

Same

> f. $(n − 1)!$ and $n!$

Lower

## Exercises 2.2 (8 points)

### 9. Problem 3 (part a,b,d,& e) (4 points)

> For each of the following functions, indicate the class $\Theta(g(n))$ the
> function belongs to. (Use the simplest g(n) possible in your answers.) Prove
> your assertions.

> a. $(n^2 + 1)^{10}$

$$
\lim_{n\to\infty} \frac{(n^2 + 1)^{10}}{n^{20}} = \\
\lim_{n\to\infty} \frac{(n^2 + 1)^{10}}{(n^2)^{10}} = \\
\lim_{n\to\infty} \left(\frac{n^2 + 1}{n^2}\right)^{10} = \\
\lim_{n\to\infty} (1 + \frac{1}{n^2})^{10} = 1
$$

$$
\therefore (n^2 + 1)^{10} \in \Theta (n^{20})
$$

> b. $\sqrt{10n^2 + 7n + 3}$

$$
\lim_{n\to\infty} \frac{\sqrt{10n^2 + 7n + 3}}{n} = \\
\lim_{n\to\infty} \sqrt{\frac{10n^2 + 7n + 3}{n^2}} = \\
\lim_{n\to\infty} \sqrt{10 + \frac{7}{n} + \frac{3}{n^2}} = \\
\sqrt{10}
$$

$$
\therefore \sqrt{10n^2 + 7n + 3} \in \Theta (n)
$$

> d. $2^{n+1} + 3^{n-1}$

$$
2^{n+1} + 3^{n-1} = \\
2^{n}2 + 3^{n}\frac{1}{3} \in \\
\Theta(2^n) + \Theta(3^n)
$$

$$
\therefore 2^{n+1} + 3^{n-1} \in \Theta (3^n)
$$

> e. $\lfloor \log_2 n \rfloor$

$$
\lfloor \log_2 n \rfloor \in \Theta(\log n)
$$

### 10. Problem 5

> List the following functions according to their order of growth from the
> lowest to the highest:

$(n-2)!$, $5\lg(n+100)^{10}$, $2^{2n}$, $0.001n^4 + 3n^3 + 1$, $\ln^2 n$,
$\sqrt[3]{n}$, $3^n$

#### Lowest to Highest Growth:

-   $5\lg(n+100)^{10}$
-   $\ln^2 n$
-   $\sqrt[3]{n}$
-   $0.001n^4 + 3n^3 + 1$
-   $3^n$
-   $2^{2n}$
-   $(n-2)!$

### 11. Problem 10

> The range of a ﬁnite nonempty set of $n$ real numbers $S$ is deﬁned as the
> difference between the largest and smallest elements of $S$. For each
> representation of $S$ given below, describe in English an algorithm to compute
> the range. Indicate the time efficiency classes of these algorithms using the
> most appropriate notation ($O$, $\Theta$, or $\Omega$).

> a. An unsorted array

Iterate the entire array to find the lowest and highest item. Then return the
difference of the two items.

**Efficiency Class:** $\Theta(n)$

> b. A sorted array

Return the difference of the last index and first index.

**Efficiency Class:** $\Theta(1)$

> c. A sorted singly linked list

Store the value of the first index in memory, iterate the entire list until you
get to the end, and finally return the difference of the first and last element.

**Efficiency Class:** $\Theta(n)$

> d. A binary search tree

First scan the binary search tree all the way to the right to locate the largest
element. Next, scan the tree all the way to the left to locate the smallest
element. Finally return the difference of the largest and smallest element.


**Efficiency Class:** $O(n)$

## Exercises 2.3 (4 points)

### 12. Problem 2

> Find the order of growth of the following sums. Use the $\Theta(g(n))$
> notation with the simplest $g(n)$ possible.

> a. $\sum_{i=0}^{n-1}(i^2 + 1)^2$

$$
\sum_{i=0}^{n-1}(i^2 + 1)^2 = \\
\sum_{i=0}^{n-1}(i^4 + 2i^2 + 1) = \\
\sum_{i=0}^{n-1}i^4 + 2\sum_{i=0}^{n-1}i^2 + \sum_{i=0}^{n-1} 1 \in \\
\Theta(n^5) + \Theta(n^3) + \Theta(n) = \\
\Theta(n^5)
$$

> b. $\sum_{i=2}^{n-1}\lg i^2$

$$
\sum_{i=2}^{n-1}\lg i^2 = \\
\sum_{i=2}^{n-1} 2 \lg i = \\
2 \sum_{i=2}^{n-1} \lg i \in \\
\Theta(n \lg n)
$$

> c. $\sum_{i=1}^n(i+1)2^{i-1}$

$$
\sum_{i=1}^n(i+1)2^{i-1} = \\
\sum_{i=1}^n 2^{i-1}i + 2^{i-1} \in \\
\Theta(2^n)
$$

> d. $\sum_{i=0}^{n-1}\sum_{j=0}^{i-1}(i+j)$

$$
\sum_{i=0}^{n-1}\sum_{j=0}^{i-1}(i+j) = \\
\sum_{i=0}^{n-1}(i + n^2) = \\
(n^2 + n^4) \in \\
\Theta(n^4)
$$

### 13. Problem 5

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

This algorithm computes the range of the input list.

> b. What is its basic operation?

Comparisons of the $i$th element to the `minval` and `maxval` in the loop.

> c. How many times is the basic operation executed?

It is executed $2(n - 1)$ times.

> d. What is the efﬁciency class of this algorithm?

$\Theta(n)$

> e. Suggest an improvement, or a better algorithm altogether, and indicate its
> efﬁciency class. If you cannot do it, try to prove that, in fact, it cannot be
> done.

A basic improvement would be to add an `else if` to the second conditional to
prevent it from checking the max value if we already know the value is lower
than the minimum value.

This would still not change the efficiency class however.

## Exercises 2.4 (6 points)

### 14. Problem 1(a,b,c)

> Solve the following recurrence relations...

> a. $x(n) = x(n - 1) + 5$ for $n > 1$, $x(1) = 0$

\begin{align*}
x(n) &= x(n - 1) + 5 \\
     &= [x(n - 2) + 5] + 5 \\
     &= [x(n - 3) + 5] + 10 \\
     &= x(n - i) + 5i
\end{align*}

let $i = (n - 1)$

\begin{align*}
x(n) &= x(n - (n - 1)) + 5(n - 1) \\
     &= x(1) + 5(n - 1) \\
     &= 0 + 5(n - 1) \\
     &= 5(n - 1)
\end{align*}

> b. $x(n) = 3x(n - 1)$ for $n > 1$, $x(1) = 4$

\begin{align*}
x(n) &= 3x(n - 1) \\
     &= 3[3x(n - 2)] \\
     &= 9[3x(n - 3)] \\
     &= 3i \times x(n - i)
\end{align*}

let $i = (n - 1)$

\begin{align*}
x(n) &= 3(n - 1) \times x(n - (n - 1)) \\
     &= 3(n - 1) \times x(1) \\
     &= 3(n - 1) \times 4 \\
     &= 12(n - 1)
\end{align*}

> c. $x(n) = x(n - 1) + n$ for $n > 0$, $x(0) = 0$

\begin{align*}
x(n) &= x(n - 1) + n \\
     &= [x(n - 2) + n] + n \\
     &= [x(n - 3) + n] + 2n \\
     &= x(n - i) + in
\end{align*}

let $i = n$

\begin{align*}
x(n) &= x(n - n) + n^2 \\
     &= x(0) + n^2 \\
     &= n^2
\end{align*}

