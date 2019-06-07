---
title: Assignment 2
author: Derek Sifford
date: 2019/06/05
---

# Exercises 3.1

## 1. Problem 4 (part a & b) (4 points)

> a. Design a brute-force algorithm for computing the value of a polynomial
> $p(x) = a_nx^n + a_{n-1}x^{n-1} + ... + a_1x a_0$ at a given point $x_0$ and
> determine its worst-case efficiency class.

```
ALGORITHM BruteForce(a[0..n], x)
    total ← a[0]
    exp ← 1
    for i← 1 to n
        exp ← exp * x
        total ← total + a[i] * exp
    return total
```

**Efficiency Class:** $\Theta(n)$

> b. If the algorithm you designed is in $\Theta(n^2)$, design a linear
> algorithm for this problem.

My solution is linear.

## 2. Problem 8 (2 point)

> Sort the list `E, X, A, M, P , L, E` in alphabetical order by selection sort.

| Iteration | State     |
| --------: | --------- |
|         0 | `EXAMPLE` |
|         1 | `AXEMPLE` |
|         2 | `AEXMPLE` |
|         3 | `AEEMPLX` |
|         4 | `AEELPMX` |
|         5 | `AEELMPX` |
|         6 | `AEELMPX` |

## 3. Problem 9 (3 points) give an example.

> Is selection sort stable?

No, selection sort is not stable because relative order is not preserved.

Consider the `5`s in the list below.

```
5 2 2 5 1
```

Swapping the `1` and the `5` on the first iteration will move the first `5` past
the second `5`.

## 4. Problem 11 (2 point)

> Sort the list E, X, A, M, P , L, E in alphabetical order by bubble sort.

| Iteration | State     |
| --------: | --------- |
|         0 | `EXAMPLE` |
|         1 | `EAXMPLE` |
|         2 | `EAMXPLE` |
|         3 | `EAMPXLE` |
|         4 | `EAMPLXE` |
|         5 | `EAMPLEX` |
|         6 | `AEMPLEX` |
|         7 | `AEMPLEX` |
|         8 | `AEMLPEX` |
|         9 | `AEMLEPX` |
|        10 | `AEMLEPX` |
|        11 | `AEMLEPX` |
|        12 | `AELMEPX` |
|        13 | `AELEMPX` |
|        14 | `AELEMPX` |
|        15 | `AELEMPX` |
|        16 | `AELEMPX` |
|        17 | `AEELMPX` |

## 5. Problem 12 (part a & b) (4 points)

> a. Prove that if bubble sort makes no exchanges on its pass through a list,
> the list is sorted and the algorithm can be stopped.

Not sure how you'd want me to prove this aside from the obvious fact that if no
exchanges occur, then it should follow that each element to the right of the
last element should be some number greater than the number it follows.

> b. Write pseudocode of the method that incorporates this improvement.

```
ALGORITHM BetterBubble(a[0..n])
    for i← 0 to n - 2
        didExchange ← false
        for j ← 0 to n - 2 - i
            if a[j+1] < a[j]
                swap a[j] and a[j+1]
                didExchange ← true
        if didExchange = false
            break
```

# Exercises 3.2

## 6. Problem 4 (2 points)

<!-- prettier-ignore-start -->
> Determine the number of character comparisons made by the brute-force
> algorithm in searching for the pattern `GANDHI` in the text
>        `THERE_IS_MORE_TO_LIFE_THAN_INCREASING_ITS_SPEED`
> Assume that the length of the text (47 chars) is known before the search starts.
<!-- prettier-ignore-end -->

Max number of comparisons if no initial match = $47 - 6 + 1 = 42$. One iteration
matches out of the $42$, but it fails immediately on the second comparison.

Thus, there are **43** comparisions.

## 7. Problem 5 (part a & b) (2 points)

> How many comparisons (both successful and unsuccessful) will be made by the
> brute-force algorithm in searching for each of the following patterns in the
> binary text of one thousand zeros?

> a. 00001

Max number of searches if no initial match = $1000 - 5 + 1 = 996$

Each iteration initially matches, and continues to match $5$ times, until it
ultimately fails.

Thus, there will be $996 * 5 = 4980$ comparisons in total.

> b. 10000

Max number of searches if no initial match = $1000 - 5 + 1 = 996$

Each initial iteration immediately fails.

Thus, there will be $996$ comparisons in total.

## 8. Problem 6 (2 points)

> Give an example of a text of length `n` and a pattern of length `m` that
> constitutes a worst-case input for the brute-force string-matching algorithm.
> Exactly how many character comparisons will be made for such input?

A simple example of this can be found in the last problem (part a).

As previously stated, there will be $4890$ comparisons.

# Exercises 3.4

## 9. Problem 2 (2 points)

> Outline an exhaustive-search algorithm for the Hamiltonian circuit problem.

Starting with a given vertex, and with a list of all vertices in the graph...

1. Arbitrarily search down an unvisited vertex, proceeding down the next
   unvisited vertex repeatedly until either there are no more moves or until we
   return to the starting vertex.
2. While searching, keep a list of visited vertices.
3. If there are no more moves, move up 1 vertex and choose another vertex and
   continue searching until an event in step 1 happens.
4. If we land at the starting vertex, check to see that all vertices have been
   visited. If not, move up 1 vertex and continue searching until an event in
   step 1 happens.
5. If there are no more paths to take, then the graph fails and is not a
   Hamiltonian circuit.

# Exercises 3.5:

## 10. Problem 1 (part a & b) (4 points)

<!-- NOTE: See associated graph image in book -->

> a. Write down the adjacency matrix and adjacency lists specifying this graph.
> (Assume that the matrix rows and columns and vertices in the adjacency lists
> follow in the alphabetical order of the vertex labels.)

|     |  a  |  b  |  c  |  d  |  e  |  f  |  g  |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|  a  |  0  |  1  |  1  |  1  |  1  |  0  |  0  |
|  b  |  1  |  0  |  0  |  1  |  0  |  1  |  0  |
|  c  |  1  |  0  |  0  |  0  |  0  |  0  |  1  |
|  d  |  1  |  1  |  0  |  0  |  0  |  1  |  0  |
|  e  |  1  |  0  |  0  |  0  |  0  |  0  |  1  |
|  f  |  0  |  1  |  0  |  1  |  0  |  0  |  0  |
|  g  |  0  |  0  |  1  |  0  |  1  |  0  |  0  |

```
[a] -> b -> c -> d -> e
[b] -> a -> d -> f
[c] -> a -> g
[d] -> a -> b -> f
[e] -> a -> g
[f] -> b -> d
[g] -> c -> e
```

> b. Starting at vertex a and resolving ties by the vertex alphabetical order,
> traverse the graph by depth-ﬁrst search and construct the corresponding
> depth-ﬁrst search tree. Give the order in which the vertices were reached for
> the ﬁrst time (pushed onto the traversal stack) and the order in which the
> vertices became dead ends (popped off the stack).

![dfs]

**Stack:**

```
f[4,1] e[7,4]
d[3,2] g[6,5]
b[2,3] c[5,6]
a[1,7]
```

## 11. Problem 4 (3 points)

> Traverse the graph of Problem 1 by breadth-ﬁrst search and construct the
> corresponding breadth-ﬁrst search tree. Start the traversal at vertex `a` and
> resolve ties by the vertex alphabetical order.

![bfs]

## 12. Problem 6 (part a & b) (6 points)

> a. Explain how one can check a graph's acyclicity by using breadth-ﬁrst
> search.

You can test for acyclicity by constructing a BFS forest of the graph. If there
are any _cross edges_ present in the forest, then you can conclude that the
graph has at least one cycle.

> b. Does either of the two traversals (DFS or BFS) always ﬁnd a cycle faster
> than the other? If you answer yes, indicate which of them is better and
> explain why it is the case; if you answer no, give two examples supporting
> your answer.

Yes, BFS will identify cycles faster because long acyclic paths would tie up the
DFS algorithm, whereas the BFS algorithm would not be tied up.

## 13. Problem 7 (part a & b)(4 points)

> Explain how one can identify connected components of a graph by using...

> a. a depth-ﬁrst search.

Starting with a list of all vertices in the graph, proceed through the the graph
using a depth-first search. Upon landing on each newly-visted vertex, remove the
vertex from the list of vertices. When search is exhausted, check the list of
vertices. If any vertices are still remaining in the list of vertices, that
means those vertices are not connected to the vertices connected to the starting
vertex.

Next, starting with a vertex from the list of remaining vertices, repeat the
process. This will identify all connected components of a graph.

> b. a breadth-ﬁrst search.

Starting with a list of all vertices in the graph, proceed through the the graph
using a breadth-first search. Upon landing on each newly-visted vertex, remove the
vertex from the list of vertices. When search is exhausted, check the list of
vertices. If any vertices are still remaining in the list of vertices, that
means those vertices are not connected to the vertices connected to the starting
vertex.

Next, starting with a vertex from the list of remaining vertices, repeat the
process. This will identify all connected components of a graph.

[dfs]: bin/dfs.png
[bfs]: bin/bfs.png
