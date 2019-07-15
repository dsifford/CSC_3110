---
title: Assignment 4
author: Derek Sifford
date: 2019/07/19
---

# Exercises 6.1

## 1. Problem 2 (4 points)

### Part a

```
ALGORITHM BruteForceIntersect(A[0..n-1], B[0..m-1])
    common = []
    for i← 0 to n-1 do
        for j← 0 to m-1 do
            if A[i] == B[j]
                common.push(A[i])
                break
    return common
```

**Efficiency class:** $O(n^2)$

### Part b

```
ALGORITHM PresortIntersect(A[0..n-1], B[0..m-1])
    sort(A)
    sort(B)
    common = []
    ai = 0
    bi = 0
    while ai <= n-1 and bi <= m-1 do
        if A[ai] < B[bi]
            ai++
        elseif A[ai] > B[bi]
            bi++
        else
            common.push(A[ai])
            ai++
            bi++
    return common
```

**Efficiency class:** $O(n \log n)$

# Exercises 6.3

## 2. Problem 4 (part a and b) (2 points)

### Part a

![2a]

### Part b

![2b]

## 3. Problem 5 (part a and b) (2 points)

### Part a

```
ALGORITHM AVLRange(Node)
    largest = Node->right
    smallest = Node->left
    while largest->right do
        largest = largest->right
    while smallest->left do
        smallest = smallest->left
    return largest - smallest
```

**Efficiency class:** $O(\log n)$

### Part b

True

# Exercises 6.4

## 4. Problem 1 (part a, b, and c) (6 points)

### Part a

```
        1
   8         6
5     3   7     4

        1
   8         7
5     3   6     4

        1
   8         7
5     3   6     4

        8
   1         7
5     3   6     4

        8
   5         7
1     3   6     4
```

### Part b

```
        1

        1                     8
   8               ==>    1

        8
   1         6

        8                     8
   1         6     ==>    5        6
5                      1

        8
   5         6
1     3

        8                     8
   5         6    ==>    5         7
1     3   7           1     3   6

        8
   5         7
1     3   6     4
```

### Part c

No

## 5. Problem 5 (part a) (2 points)

### Part a

```
ALGORITHM DeleteMinItem(A[0..n-1])
    smallestIdx = floor((n-1)/2)
    smallest = A[smallestIdx]
    for i = floor((n-1)/2) + 1 to n-1 do
        if A[i] < smallest
            smallestIdx = i
            smallest = A[i]
    swap(A[smallestIdx], A[n-1])
    heapify(A[0..n-2])
```

**Time Efficiency:** $(O(n \log n))$

## 6. Problem 7 part a, c (4 points)

### Part a

```
# Construction
[1 2 3 4 5]
[1 5 3 4 2]
[5 1 3 4 2]
[5 4 3 1 2]

# Sort
[5 4 3 1 2 |]
[4 3 1 2 | 5]
[3 1 2 | 4 5]
[2 1 | 3 4 5]
[1 | 2 3 4 5]
[| 1 2 3 4 5]
```

### Part b

```
# Construction
[5 4 3 2 1]

# Sort
[5 4 3 2 1 |]
[4 3 2 1 | 5]
[3 2 1 | 4 5]
[2 1 | 3 4 5]
[1 | 2 3 4 5]
[| 1 2 3 4 5]
```

### Part c

```
# Construction
[S O R T I N G]
[S T R O I N G]
[T S R O I N G]
[T S R O I N G]

# Sort
[T S R O I N G |]
[R S O I N G | T]
[S O I N G | R T]
[O I N G | S R T]
[I N G | O S R T]
[N I G | O S R T]
[I G | N O S R T]
[G | I N O S R T]
[| G I N O S R T]
```

# Exercises 6.5

## 7. Problem 4 (2 points)

### Part a

\begin{align*} p(x) &= 3x^4 - x^3 + 2x + 5 \\ &= x(3x^3 - x^2 + 2) + 5 \\ &=
x(x(3x^2 - x) + 2) + 5 \\ &= x(x(x(3x - 1)) + 2) + 5 \\ p(2) &= 2(2(2(6 -
1)) + 2) + 5 = 49 \end{align*}

### Part b

Yes.

## 8. Problem 7 (2 points)

### Part a

|                      |     |       |       |       |                  |
| -------------------- | :-: | :---: | :---: | :---: | :--------------: |
| binary digits of $n$ |  1  |   0   |   0   |   0   |        1         |
| product accumulator  | $a$ | $a^2$ | $a^4$ | $a^8$ | $a^{16} \cdot a$ |

### Part b

Yes.

## 9. Problem 8 (2 points)

|                           |       |       |       |     |                      |
| :-----------------------: | :---: | :---: | :---: | :-: | -------------------- |
|             1             |   0   |   0   |   0   |  1  | binary digits of $n$ |
|         $a^{16}$          | $a^8$ | $a^4$ | $a^2$ |  a  | terms $a^{2^i}$      |
| $a^{16} \cdot a = a^{17}$ |       |       |       |  a  | product accumulator  |

# Exercises 6.6

## 10. Problem 2 (2 points)

This is essentially the exact same algorithm, except in this case, the "heapify"
step reverses the comparison operator such that the lower value is moved up.

# Exercises 7.1

## 11. Problem 3 (4 points)

```
            D[a..d]
A[7] = b [2][5][7][8]  [ ][ ][ ][ ][b][ ][ ][ ]
A[6] = a [2][4][7][8]  [ ][a][ ][ ][ ][ ][ ][ ]
A[5] = a [1][4][7][8]  [a][ ][ ][ ][ ][ ][ ][ ]
A[4] = b [0][4][7][8]  [ ][ ][ ][b][ ][ ][ ][ ]
A[3] = c [0][3][7][8]  [ ][ ][ ][ ][ ][ ][c][ ]
A[2] = d [0][3][6][8]  [ ][ ][ ][ ][ ][ ][ ][d]
A[1] = c [0][3][6][7]  [ ][ ][ ][ ][ ][c][ ][ ]
A[0] = b [0][3][5][7]  [ ][ ][b][ ][ ][ ][ ][ ]
```

\pagebreak

# Exercises 7.2

## 12. Problem 2 (4 points)

### Part a

| character $c$ |  A  |  C  |  G  |  T  |
| :-----------: | :-: | :-: | :-: | :-: |
| shift $t(c)$  |  5  |  2  | 10  |  1  |

### Part b

```
TTATAGATCTCGTATTCTTTTATAGATCTCCTATTCTT
TCCTATTCTT
 TCCTATTCTT
   TCCTATTCTT
    TCCTATTCTT
         TCCTATTCTT
          TCCTATTCTT
           TCCTATTCTT
            TCCTATTCTT
                 TCCTATTCTT
                  TCCTATTCTT
                    TCCTATTCTT
                      TCCTATTCTT
                       TCCTATTCTT
                            TCCTATTCTT
```

\pagebreak

# Exercises 7.3

## 13. Problem 2 (4 points)

### Part a

| keys           | 30  | 20  | 56  | 75  | 31  | 19  |
| -------------- | :-: | :-: | :-: | :-: | :-: | :-: |
| hash addresses |  8  |  9  |  1  |  9  |  9  |  8  |

|  0  |  1  |  2  |  3  |  4  |  5  |  6  |  7  |  8  |  9  | 10  | 11  |
| :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: | :-: |
|     |     |     |     |     |     |     |     | 30  |     |     |     |
|     |     |     |     |     |     |     |     | 30  | 20  |     |     |
|     | 56  |     |     |     |     |     |     | 30  | 20  |     |     |
|     | 56  |     |     |     |     |     |     | 30  | 20  | 75  |     |
|     | 56  |     |     |     |     |     |     | 30  | 20  | 75  | 31  |
| 19  | 56  |     |     |     |     |     |     | 30  | 20  | 75  | 31  |

### Part b

The largest number of key comparisons for a successful search is $5$ (using key $19$).

### Part c

The average number of key comparisons for a successful search is $\frac{1 + 1 + 1 + 2 + 3 + 5}{6} = 2.16 \approx 2$.

[2a]: bin/2a.png
[2b]: bin/2b.png
