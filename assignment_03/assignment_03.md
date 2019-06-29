---
title: Assignment 3
author: Derek Sifford
date: 2019/07/01
---

# Exercises 4.1

## 1. Problem 5 (2 points)

No, this algorithm does not work correctly. This can be realized when we
consider what, by definition, an adjacency matrix of a connected graph looks
like.

For the sake of example, consider a connected graph of 4 nodes. The adjacency
matrix for this graph would like as follows:

```
0 1 1 1
1 0 1 1
1 1 0 1
1 1 1 0
```

Now, if we look at the innermost `if` statement, we can see that if _any_ node
in the tree is connected (i.e. contains a `1`), then that row is considered
connected and all other nodes for that row are ignored. That is wrong.

Instead, the check should consider all nodes of a row whose index is not equal
to the comparing column. If _all_ of the nodes are connected, then _that_ should
be considered a pass and `1` should be returned.

## 2. Problem 7 (1 point)

|       |       |       |       |       |       |       |
| :---: | :---: | :---: | :---: | :---: | :---: | :---: |
| **E** |   X   |   A   |   M   |   P   |   L   |   E   |
| **E** | **X** |   A   |   M   |   P   |   L   |   E   |
| **A** | **E** | **X** |   M   |   P   |   L   |   E   |
| **A** | **E** | **M** | **X** |   P   |   L   |   E   |
| **A** | **E** | **M** | **P** | **X** |   L   |   E   |
| **A** | **E** | **L** | **M** | **P** | **X** |   E   |
| **A** | **E** | **E** | **L** | **M** | **P** | **X** |

## 3. Problem 9 (2 point)

Yes, it is definitely possible to implement insertion sort for linked lists,
assuming we are talking about doubly linked lists.

If so, then the time efficiency would be identical to the time efficiency of an
array implementing insertion sort. The only difference is that instead of
keeping track of an _index_, you'd instead be keeping track of a pointer to the
current node in the list.

# Exercises 4.2

## 4. Problem 1 (3 points)

### Part a.

**DFS Traversal Stack:**

```
   f2
e1 g3
b4    c5
a6       d7
```

**Topological Sort Order:** `d`, `a`, `c`, `b`, `g`, `f`, `e`

### Part b.

**DFS Traversal Stack:**

```
e1
g2
d3
c4
b5
a6 f7
```

**Topological Sort Order:** `f`, `a`, `b`, `c`, `d`, `g`, `e`

## 5. Problem 5 (2 points)

### Part a.

```
   a     b
c     d     e
   f     g
```

```
   a     b
c           e
   f     g
```

```
         b
c           e
   f     g
```

```

c           e
   f     g
```

```

            e
   f     g
```

```

            e
   f
```

```


   f
```

**Topological Sort Order:** `d`, `a`, `b`, `c`, `g`, `e`, `f`

### Part b.

```
a     b     c     d
   e     f     g
```

```
a     b     c     d
   e           g
```

```
      b     c     d
   e           g
```

```
            c     d
   e           g
```

```
                  d
   e           g
```

```

   e           g
```

```

   e
```

**Topological Sort Order:** `f`, `a`, `b`, `c`, `d`, `g`, `e`

## 6. Problem 9 (part a) (4 points)

**DFS Traversal Stack:**

```
f1
g2    h6
b3 d5 e7
a4 c8
```

**DFS Traversal Stack (reversed):**

```
e1
h2
c3
d4
b5
g6
f7
a8
```

There are no strongly connected components.

# Exercises 4.3

## 7. Problem 2 (part a and b) (4 points)

### Part a.

```
              1
          12      21
     123     132     312
     213     231     321
1234    1243    1423    4123
1324    1342    1432    4132
3124    3142    3412    4312
2134    2143    2413    4213
2314    2341    2431    4231
3214    3241    3421    4321
```

### Part b.

```
<1 <2 <3 <4
<1 <2 <4 <3
<1 <4 <2 <3
<4 <1 <2 <3
4> <1 <3 <2
<1 4> <3 <2
<1 <3 4> <2
<1 <3 <2 4>
<3 <1 <2 <4
<3 <1 <4 <2
<3 <4 <1 <2
<4 <3 <1 <2
4> 3> <2 <1
3> 4> <2 <1
3> <2 4> <1
3> <2 <1 4>
<2 3> <1 <4
<2 3> <4 <1
<2 <4 3> <1
<4 <2 3> <1
4> <2 <1 3>
<2 4> <1 3>
<2 <1 4> 3>
<2 <1 3> 4>
```

## 8. Problem 7 (3 points)

```
ALGORITHM BitString(n, result = "")
    // Recursive algorithm generating all 2^n bit strings of length n
    // Input: A positive integer n.
    if n <= 1
        return "1" + result;
    else
        return BitString(n - 1, "0" + result);
```

# Exercise 4.4

## 9. Problem 1 (3 points)

```
ALGORITHM CutStick(stick)
    // Input.stick: A stick n inches long.
    // Assume Cut(stick, n) returns a tuple of (left, right) portions
    n = len(stick)
    if n == 1
        return stick
    if n mod 2 == 0
        (left, right) = Cut(stick, n / 2)
    else
        (left, right) = Cut(stick, (n / 2) + 1)
    return CutStick(left) + CutStick(right)
```

Minimum cuts = $n - 1$

**Note:** The problem is not clear. Not sure what the author means by "several
pieces can be cut at the same time". So please "cut" me some slack here.

## 10. Problem 4 (1 point)

A binary search's time efficiency is $O(\log n)$ whereas a sequential search's
time efficiency is $O(n)$.

Average case of binary search = $\log(1000000)$ = $6$.

Average case of sequential search = $1000000/2$ = $500000$.

Thus, binary search is $500000/6 = 83333$ times faster.

## 11. Problem 11 (2 points)

### Part a

|   n |   m |     |
| --: | --: | --: |
|  26 |  47 |     |
|  13 |  94 |  94 |
|   6 | 188 |     |
|   3 | 376 | 376 |
|   1 | 752 | 752 |

$94 + 376 + 752 = 1222$

### Part b

Yes, it matters. You should pick the smaller number for `n` so that it reduces
to $1$ faster.

## 12. Problem 13 (1 point)

```
40 in binary = 101000

Left circular bit shift of 101000 = 010001 = 10001

10001 to binary is 17
```

$J(40) = 17$

# Exercise 4.5

## 13. Problem 2 (2 point)

**Notes:**

-   Length = 7
-   Middle number = $Ceil(7/2)$ = $4$

```
 0  1  2  3  4  5  6
--------------------
 9 12  5 17 20 30  8
 9  5 12 17 20 30  8
 9  5  8 17 20 30 12
 8  5  9 17 20 30 12
         17 20 30 12
         17 12 30 20
         12 17 30 20
```

**Median:** 12

# Exercises 5.1

## 14. Problem 3 (part a, b, and c) (6 points)

### Part a

```
ALGORITHM Exp(a, n)
    // Input.a: base number
    // Input.n: exponent
    if n == 1
        return a
    return a * Exp(a, n - 1)
```

### Part b

```
T(1) = c
T(n) = c + T(n-1)
     = 2c + T(n-2)
     = 3c + T(n-3)
T(2) = 2 = n
```

\begin{align*} T(1) &= c \\ T(n) &= c + T(n-1) \\ &= 2c + T(n-2) \\ &= 3c +
T(n-3) \\ T(2) &= 2 = n \end{align*}

Thus, this is $O(n)$

### Part c

This is pretty much identical to the brute force, assuming the only difference
of the brute force is using a for loop, rather than recursion.

## 15. Problem 5 (part a, b, and c) (3 points)

a) $\Theta(n^{\log_{2}4})$

b) $\Theta(n^2 \log n)$

c) $\Theta(n^3)$

## 16. Problem 6 (2 points)

```
         [EXAMPLE]
       [EXAM] [PLE]
     [EX] [AM] [PL] [E]
[E] [X] [A] [M] [P] [L] [E]
  [EX]    [AM]    [LP]  [E]
     [AEMX]         [ELP]
         [AEELMPX]
```

# Exercises 5.2

## 17. Problem 3 (1 points)

Consider the following list of numbers.

```
    i           j
[5][2][3][5][8][9]
 ^ pivot
 0  1  2  3  4  5
```

Upon scanning, this the first position of when a swap occurs is as follows:

```
          j
          i
[5][2][3][5][8][9]
 ^ pivot
 0  1  2  3  4  5
```

At this point, we would then swap the pivot (index 0) with index 3.

By doing this, we have altered the order of two elements that are equal which
makes this unstable.

## 18. Problem 5 (2 points)

a) Worst-case

b) Worst-case

## 19. Problem 8 (3 points)

**Note:** This is quite possibly the worst question ever written. My
interpretation of this god-awful question is that it the solution for this is a
list with all negative values on the left (in any order) and all positive
elements on the right (again, not sorted and in any order). With that assumption
in mind...

```
ALGORITHM UselessSort(A[l..r])
    // Input: Array or subarray to be processed.
    i = l
    j = r
    while i <= j
        if A[i] < 0
            i++
        else
            swap(A[i], A[j])
            j--
```
