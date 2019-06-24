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
    if n less than or equal to 1
        return "1" + result;
    else
        return BitString(n - 1, "0" + result);
```

# Exercise 4.4

## 9. Problem 1 (3 points)

## 10. Problem 4 (1 point)

A binary search's time efficiency is $O(\log n)$ whereas a sequential search's time efficiency is $O(n)$.

Average case of binary search = $\log(1000000)$ = $6$.

Average case of sequential search = $1000000/2$ = $500000$.

Thus, binary search is $500000/6 = 83333$ times faster.

## 11. Problem 11 (2 points)

## 12. Problem 13 (1 point)

# Exercise 4.5

## 13. Problem 2 (2 point)

# Exercises 5.1

## 14. Problem 3 (part a, b, and c) (6 points)

## 15. Problem 5 (part a, b, and c) (3 points)

## 16. Problem 6 (2 points)

# Exercises 5.2

## 17. Problem 3 (1 points)

## 18. Problem 5 (2 points)

## 19. Problem 8 (3 points)
