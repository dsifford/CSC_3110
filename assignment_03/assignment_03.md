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

## 5. Problem 5 (2 points)

## 6. Problem 9 (part a) (4 points)

# Exercises 4.3

## 7. Problem 2 (part a and b) (4 points)

## 8. Problem 7 (3 points)

# Exercise 4.4

## 9. Problem 1 (3 points)

## 10. Problem 4 (1 point)

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
