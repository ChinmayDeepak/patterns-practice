# Python Pattern Printing — My Solutions

A collection of **15 Python pattern-printing problems** I solved while practicing loops, conditionals, string manipulation, and 2D lists.

> All Python solutions below are from my own practice. I've retained my original logic rather than replacing it with alternative approaches.

## Table of Contents

1. [Pyramid Pattern](#pattern-1)
2. [Reverse Pyramid Pattern](#pattern-2)
3. [Diamond Pattern](#pattern-3)
4. [Half Diamond Pattern](#pattern-4)
5. [Alternating 0–1 Triangle](#pattern-5)
6. [Number Crown Pattern](#pattern-6)
7. [Floyd's Triangle](#pattern-7)
8. [Hollow Pyramid Pattern](#pattern-8)
9. [Hollow Diamond Pattern](#pattern-9)
10. [Alphabet Palindrome Pyramid](#pattern-10)
11. [Reverse Alphabet Triangle](#pattern-11)
12. [Butterfly Pattern — 2n Rows](#pattern-12)
13. [Butterfly Pattern — 2n − 1 Rows](#pattern-13)
14. [Star Diamond](#pattern-14)
15. [Concentric Number Square](#pattern-15)

---

<a id="pattern-1"></a>

## 1. Pyramid Pattern

```python
def pattern(n):
    for i in range(n):
          print(' '*(n-i-1),'*'*(2*i+1),' '*(n-i-1) )

pattern(6)
```

Star counts increase by two on each row.

---

<a id="pattern-2"></a>

## 2. Reverse Pyramid Pattern

```python
def pattern(n):
    for i in range(n):
          print(' '*(i),'*'*(2*n-(2*i+1)),' '*(i))

pattern(6)
```

Star counts decrease by two on each row.

---

<a id="pattern-3"></a>

## 3. Diamond Pattern

```python
def pattern(n):
    for i in range(n):
      if i<n//2:
          print(' '*(n-i-1),'*'*(2*i+1),' '*(n-i-1) )
      else:
        print(' '*(i),'*'*(2*n-(2*i+1)),' '*(i))

pattern(9)
```

Uses a single loop and an `if/else` to form the two halves. This version was tested with `n = 9`; because of the spaces automatically added by `print()`, the output includes extra whitespace.

---

<a id="pattern-4"></a>

## 4. Half Diamond Pattern

```python
def pattern(n):
    for i in range(1,2*n):
      if i<2*n//2:
        print("*"*i)
      else:
        print("*"*(2*n-i))

pattern(5)
```

Output:

```text
*
**
***
****
*****
****
***
**
*
```

---

<a id="pattern-5"></a>

## 5. Alternating 0–1 Triangle

```python
def pattern(n):
    for i in range(1,n+1):
      if i%2!=0:
        for j in range(1,i+1):
          if j%2!=0:
            print("1 ",end="")
          else:
            print("0 ",end="")
        print()
      else:
        for j in range(1,i+1):
          if j%2!=0:
            print("0 ",end="")
          else:
            print("1 ",end="")
        print()

pattern(5)
```

Output:

```text
1
0 1
1 0 1
0 1 0 1
1 0 1 0 1
```

---

<a id="pattern-6"></a>

## 6. Number Crown Pattern

```python
def pattern(n):
    for i in range(1,n+1):
      s=""
      for j in range(1,i+1):
        s+=str(j)
      print(str(s)+" "*(2*n-2*i)+s[::-1],end="")
      print()

pattern(4)
```

Output:

```text
1      1
12    21
123  321
12344321
```

This solution builds the ascending part as a string and uses `[::-1]` for the other side. It is intended for single-digit rows (`n <= 9`).

---

<a id="pattern-7"></a>

## 7. Floyd's Triangle

```python
def pattern(n):
    num=0
    for i in range(1,n+1):
      for j in range(1,i+1):
        num=num+1
        print(num,end="")
      print()

pattern(5)
```

Output:

```text
1
23
456
78910
1112131415
```

This is exactly how I originally printed it, without adding separators between numbers.

---

<a id="pattern-8"></a>

## 8. Hollow Pyramid Pattern

```python
def pattern(n):
 j=-1
 for i in range(1,n+1):
   print(" "*(n-i),end="")
   if i==1:
     print("*")
   elif i==n:
     print("*"*(2*n-1))
   else:
     j=j+1
     print("*"+" "*(2*j+1)+"*")
pattern(7)
```

Output:

```text
      *
     * *
    *   *
   *     *
  *       *
 *         *
*************
```

---

<a id="pattern-9"></a>

## 9. Hollow Diamond Pattern

```python
def pattern(n):
  j=-1
  for i in range(1,2*n):
    if i<=n:
      print(" "*(n-i),end="")
      if i==1:
        print("*")
      else:
        j=j+1
        print("*"+" "*(2*j+1)+"*")
        k=2*j+1
    else:
      k=k-2
      print(" "*(i-n),end="")
      if i==2*n-1:
        print("*")
      else:
        print("*"+" "*(k)+"*")

pattern(4)
```

Output:

```text
   *
  * *
 *   *
*     *
 *   *
  * *
   *
```

---

<a id="pattern-10"></a>

## 10. Alphabet Palindrome Pyramid

**My code:**

```python
def pattern(n):
    alpha=65
    s=""
    mid=chr(alpha)
    for i in range(1,n+1):
        print(" "*(n-i)+s+mid+s[::-1]+" "*(n-i),end="")
        s+=chr(alpha)
        alpha=alpha+1
        mid=chr(alpha)
        print()

pattern(4)
```

**Output:**

```text
   A
  ABA
 ABCBA
ABCDCBA
```

---

<a id="pattern-11"></a>

## 11. Reverse Alphabet Triangle

**My code:**

```python
def pattern(n):
    s=""
    alpha=65
    for i in range(1,n+1):
        s+=chr(alpha+n-i)
        print(s[::-1])

pattern(5)
```

**Output:**

```text
E
DE
CDE
BCDE
ABCDE
```

---

<a id="pattern-12"></a>

## 12. Butterfly Pattern — 2n Rows

**My code:**

```python
def pattern(n):
    j=0
    for i in range(0,2*n):
        if i<2*n//2:
            print("*"*(n-i)+" "*(2*i)+"*"*(n-i))
        else:
            j=j+1
            print("*"*(j)+" "*(2*n-2*j)+"*"*(j))

pattern(5)
```

**Output** (spaces displayed as `·`):

```text
**********
****··****
***····***
**······**
*········*
*········*
**······**
***····***
****··****
**********
```

---

<a id="pattern-13"></a>

## 13. Butterfly Pattern — 2n − 1 Rows

**My code:**

```python
def pattern(n):
    j=0
    for i in range(1,2*n):
        if i<=n:
            print("*"*i+" "*(2*n-2*i)+"*"*i)
        else:
            j=j+1
            print("*"*(n-j)+" "*2*j+"*"*(n-j))

pattern(7)
```

**Output** (spaces displayed as `·`):

```text
*············*
**··········**
***········***
****······****
*****····*****
******··******
**************
******··******
*****····*****
****······****
***········***
**··········**
*············*
```

---

<a id="pattern-14"></a>

## 14. Star Diamond

**My code:**

```python
n = 5
j=-1
for i in range(1, 2*n+1):
    if i<=n:
        print(" "*(n-i)+"* "*(i))
    else:
        j=j+1
        print(" "*j+"* "*(n-j))
```

**Output:**

```text
    *
   * *
  * * *
 * * * *
* * * * *
* * * * *
 * * * *
  * * *
   * *
    *
```

---

<a id="pattern-15"></a>

## 15. Concentric Number Square

**My code:**

```python
def pattern(n):
    a=[]
    for i in range(2*n-1):
        s=0
        a.append([s]*(2*n-1))
    nj=0
    ni=2*n-1
    for k in range(n, 0, -1):
        for i in range(0+nj,ni):
            for j in range(0+nj,ni):
                a[i][j]=k
        ni=ni-1
        nj=nj+1

    for i in range(len(a)):
        for j in range(len(a[0])):
            print(a[i][j],end="")
        print()

pattern(4)
```

**Output:**

```text
4444444
4333334
4322234
4321234
4322234
4333334
4444444
```

### InterviewBit PrettyPrint submission

The same concentric-square approach, returning a 2D list instead of printing:

```python
class Solution:
    # @param A : integer
    # @return a list of list of integers
    def prettyPrint(self,n):
        a=[]
        for i in range(2*n-1):
            s=0
            a.append([s]*(2*n-1))
        nj=0
        ni=2*n-1
        for k in range(n, 0, -1):
            for i in range(0+nj,ni):
                for j in range(0+nj,ni):
                    a[i][j]=k
            ni=ni-1
            nj=nj+1
        return a
```

---

## Concepts Practiced

- `for` loops, nested loops, and `if` / `else` conditions
- `range()`, integer division (`//`), and modulo (`%`)
- String repetition, concatenation, and `[::-1]` reversal
- Managing `print()` with `end=""`
- Incrementing and decrementing counters across rows
- Creating and updating 2D lists for concentric patterns

## How to Run

Each section is an independent Python 3 example. Copy one snippet to a file such as `pattern.py` and run:

```bash
python pattern.py
```

The included **InterviewBit `prettyPrint`** implementation returns a 2D list and is an additional version of pattern 15, not a separate pattern.

---

*My Python pattern-printing practice collection.*
