![](http://fondinfo.github.io/images/comp/chess.jpg)
# Computational Complexity
## Introduction to Computer Science <br> Michele Tomaiuolo @ Ingegneria UniPR

---

# 💡️ Problems and Complexity

- *Unsolvable* problems
    - E.g., This sentence is false
    - Gödel's incompleteness; halting undecidability
- Solvable
    - *Intractable* (exponential cost)
    - Tractable (acceptable, "polynomial" cost) <br>  
- **Computability**: classifying solvable and unsolvable problems
- **Complexity**: "easy" and "difficult"

---

![](http://fondinfo.github.io/images/comp/catalogue.png)
# 🧪 Linear Search

- Search in a not necessarily sorted list (*array*)
- For homogeneity: algorithms in these slides all operate in the interval `[beg, end)`

``` py
def linear_search(v: list, value, beg, end) -> int:
    for i in range(beg, end):
        if v[i] == value:
            return i
    return -1
```

>

<https://fondinfo.github.io/play/?c20_complexity.py>

---

![large](http://fondinfo.github.io/images/comp/binary-search.svg)
# 🧪 Binary Search

- Search in a sorted list

``` py
def binary_search(v: list, value, beg, end) -> int:
    if end - beg <= 0:
        return -1
    mid = (beg + end) // 2
    if v[mid] > value:
        return binary_search(v, value, beg, mid)
    elif v[mid] < value:
        return binary_search(v, value, mid + 1, end)
    return mid
```

>

<https://fondinfo.github.io/play/?c20_complexity.py>

---

# 💡️ Algorithm Cost

- **Space**, required in memory
- **Time**, needed for execution
- Usually, cycles are counted as a function of `$n$`
- Or comparisons/swaps between array elements
    - Array in main memory, slow access
    - Other variables in processor registers
- Empirical tests and measurements

>

<http://www.stroustrup.com/Software-for-infrastructure.pdf#page=5>
<br>
<https://www.youtube.com/watch?v=YQs6IC-vgmo>

---

# ⭐ Algorithm Comparison

- Worst case for search: element not present
- Linear search: **`$n$`** comparisons
- Binary search: ~ **`$\log_2(n)$`** comparisons
    - At each iteration, dimension `$n$` is halved
    - `$n, ⌊\frac{n}{2}⌋, ⌊\frac{n}{4}⌋, \dots, ⌊\frac{n}{2^{k-1}}⌋$` at iteration `$k$`
    - Finally `$⌊\frac{n}{2^{k-1}}⌋ = 1 \Rightarrow k = 1 + ⌊\log_2(n)⌋$`

---

# 💡️ Complexity Definition

- A function `$f(n)$` has *order* `$O(g(n))$` if and only if:
    - `$\exists c>0, m>0 : \forall n > m, |f(n)| \leq c|g(n)|$`
- An algorithm has a *complexity* `$O(g(n))$` if and only if:
    - `$t(n)$` has order `$O(g(n))$`
    - `$t(n)$`: computation time of the algorithm <br> with each instance*✶* of size `$n$`
- "Complexity" is therefore determined by the *worst case*
    - One can also study "average case complexity" <br> and "best case complexity"

>

✶ Instance: set of data on which the problem is defined

---

![](http://fondinfo.github.io/images/comp/orders.svg)
# 💡️ Asymptotic Analysis

- For `$n$` sufficiently large, up to a multiplicative constant, `$f(n)$` does not exceed `$g(n)$` in absolute value
- Algorithm behavior at the limit, as instance size tends to infinity
- E.g., `$n$` = 1,000,000
    - Linear search: 1,000,000 cycles
    - Binary search: 20 cycles

---

# 💡️ Intrinsic Complexity

- Lower bound of a problem's complexity
- A function `$f(n)$` is `$\Omega(g(n))$` if and only if
    - `$\exists c>0, m>0 : \forall n > m, |f(n)| ≥ c|g(n)|$`
- A problem has a *lower bound* on complexity `$\Omega(g(n))$` if and only if
    - For every solving algorithm…
    - $\exists$ an instance (worst case)…
    - for which the computation time `$t(n)$` is `$\Omega(g(n))$`

---

# ⭐ Optimal Algorithm

- An algorithm that solves problem `$P$`, with the following two conditions:
    - Execution cost `$O(g(n))$`
    - `$P$` has a lower bound `$\Omega(g(n))$`
- Problem of *searching* in sorted lists
    - It is proven that the intrinsic complexity is **`$\log_2(n)$`**
    - ⇒ The binary search algorithm is optimal
- But linear search also works for unsorted lists!

---

# Sorting Algorithms

---

# ⭐ Sorting Algorithms

- Binary search: important to have sorted data
    - *“Ordinateur”, “ordenador”*
- *Simple*, iterative sorting algorithms
    - Complexity `$n^2$`
    - Comparison between each element and the others
- *Divide and conquer*, recursive sorting algorithms
    - Complexity `$n\log_2(n)$`
    - Intrinsic complexity of the problem
- Remember that `$\log_a(n) = \frac{\log_b(n)}{\log_b(a)}$`, with `${\log_b(a)}$` constant ([proof](https://en.wikipedia.org/wiki/Logarithm#Change_of_base))
    - ⇒ The base of the logarithm does not change complexity

---

![large](http://fondinfo.github.io/images/comp/bubble-sort.svg)
# 🧪 Bubble Sort

``` py
def swap(v: list, i: int, j: int):
    v[i], v[j] = v[j], v[i]

def bubble_sort(v: list, beg, end):
    ##last_swap = 0
    for i in range(beg, end - 1):
        if v[i] > v[i + 1]:
            swap(v, i, i + 1)  ##last_swap = i + 1
    end -= 1  ##end = last_swap
    if end - beg > 1:
        bubble_sort(v, beg, end)  # loop
```

>

<https://fondinfo.github.io/play/?c20_complexity.py>
<br>
<https://visualgo.net/en/sorting?slide=7>
<br>
<https://www.youtube.com/watch?v=lyZQPjUT5B4>

---

![](http://fondinfo.github.io/images/hist/1840-gauss.png) `$$\sum_{k=1}^n k = \frac{n(n+1)}{2}$$` “Gauss’ trick”
# ⭐ Bubble Sort Analysis

``` py
vals = [38, 27, 43, 3, 9, 82, 10]
bubble_sort(vals, 0, len(vals))
```

- Larger elements emerge quickly
    - *“Like champagne bubbles”*
- Worst case: reversed list
    - Number of comparisons and swaps
    - `$(n-1)+(n-2)+...+2+1 = \\ = \frac{n(n-1)}{2} ≈ \frac{n^2}{2}, n→\infty$`
    - Complexity **`$O(n^2)$`**
- Also on average, approximately same values

---

![large](http://fondinfo.github.io/images/comp/selection-sort.svg)
# 🧪 Selection Sort

``` py
def find_minimum(v: list, beg, end):
    min_pos = beg
    for i in range(beg + 1, end):
        if v[i] < v[min_pos]:
            min_pos = i
    return min_pos

def selection_sort(v: list, beg, end):
    if end - beg <= 1:
        return
    min_pos = find_minimum(v, beg, end)
    swap(v, min_pos, beg)
    selection_sort(v, beg + 1, end)  # loop
```

>

<https://fondinfo.github.io/play/?c20_complexity.py>
<br>
<https://visualgo.net/en/sorting?slide=8>

---

# ⭐ Selection Sort Analysis

- At each main loop, the smallest value is selected
- Worst case: reversed list
    - Number of comparisons `$\frac{n(n-1)}{2}$`
    - Complexity **`$O(n^2)$`**
    - Number of swaps: `$n-1$` swaps
- Also on average, approximately same values

>

Number of comparisons (Gauss's trick applies): <br>
`$(n - 1) + (n - 2) + (n - 3) + ... + 0$`

---

![large](http://fondinfo.github.io/images/comp/insertion-sort.svg)
# 🧪 Insertion Sort

``` py
def insertion_sort(v: list, beg, end, mid=1):
    if end - mid <= 0:
        return
    i, value = mid, v[mid]
    # find value's place, at its left
    while i > beg and v[i - 1] > value:
        v[i] = v[i - 1]  # shift right
        i -= 1
    v[i] = value
    insertion_sort(v, beg, end, mid + 1)  # loop
```


>

<https://fondinfo.github.io/play/?c20_complexity.py>
<br>
<https://visualgo.net/en/sorting?slide=9>

---

# ⭐ Insertion Sort Analysis

- The first part is sorted, elements are inserted one at a time, making it easier to find their place
- Worst case: reversed list
    - Cycles: `$1+2+...+(n-1) = \frac{n(n-1)}{2}$`
    - Complexity **`$O(n^2)$`**
- On average, only half of the first part is traversed
    - On average `$\frac{n^2}{4}$` comparisons and `$\frac{n^2}{4}$` swaps
- Optimizations
    - Binary search in sorted part, but swaps
    - Insertion in pairs, or groups

---

![](http://fondinfo.github.io/images/comp/quick-sort.svg) ![large](http://fondinfo.github.io/images/comp/quick-sort.png)
# 🧪 Quick Sort

``` py
def quick_sort(v: list, beg, end):
    if end - beg <= 1:
        return
    mid = beg
    for i in range(beg, end):
        if v[i] <= v[end - 1]:  # last val as pivot
            swap(v, i, mid)
            mid += 1
    quick_sort(v, beg, mid - 1)
    quick_sort(v, mid, end)
```

>

<https://www.youtube.com/watch?v=ywWBy6J5gz8>
<br>
<https://visualgo.net/en/sorting?slide=12>

---

![large](http://fondinfo.github.io/images/comp/quick-sort-best.svg)
# ⭐ Quick Sort Best Case

- ➊ Choose a `pivot` value (last?)
- ➋ → Two parts
    - `val≤pivot`; `val>pivot`
    - `$n-1$` comparisons and swaps
- ➌ Same algorithm on the 2 parts (recursion)
- Complexity *best case, or average* : **`$O(n\log_2 n)$`**
    - *If* the pivot is approximately median…
    - At each step the size is halved
    - After `$k$` steps: `$2^k$` lists of size `$\frac{n}{2^k}$`
    - Finally, `$k=\log_2 n$`: `$n$` lists of size `$1$`

---

![large](http://fondinfo.github.io/images/comp/quick-sort-worst.svg)
# ⭐ Quick Sort Worst Case

- Complexity *worst case* : **`$O(n^2)$`**
    - List already sorted, or reversed
    - All elements end up on the same side of the pivot
- The worst case depends on pivot choice
    - But it always exists

---

![](http://fondinfo.github.io/images/comp/merge.svg)
# 🧪 Merge, with auxiliary memory

- Merge of *sorted* lists: **linear** cost
    - Compare the 2 elements at the head
    - Take the smaller one

``` py
def merge(v1: list, b1, e1,  # beg, end
          v2: list, b2, e2) -> list:
    result = []  # required extra memory
    while b1 < e1 or b2 < e2:
        if b1 < e1 and (b2 == e2 or v1[b1] <= v2[b2]):
            result.append(v1[b1]); b1 += 1
        else:
            result.append(v2[b2]); b2 += 1
    return result
```

---

![large](http://fondinfo.github.io/images/comp/merge-sort.svg) Split in red; merge in green
# 🧪 Merge Sort

- **Divide...** - *Split* always in half
- **et impera** - *Merge* of sorted lists
- Each *merge* level has cost `$\propto n$`
    - `$n, 2\cdot\frac{n}{2}, 4\cdot\frac{n}{4}, \dots, 2^k\cdot\frac{n}{2^k}$`
- `$\log_2(n)$` levels of *merge* are needed

``` py
def merge_sort(v: list, beg, end: int):
    if end - beg <= 1: return
    mid = (beg + end) // 2
    merge_sort(v, beg, mid)
    merge_sort(v, mid, end)
    v[beg:end] = merge(v, beg, mid, v, mid, end)
```

>

<https://visualgo.net/en/sorting?slide=11>

---

# ⭐ Merge Sort Analysis

- Similar to Quick Sort, but no pivot is chosen
- Merging has linear complexity
- Worst case, average case: **`$O(n\log_2 n)$`**
- **Space**: merging requires additional memory: `$n$`
    - This cost can be avoided with *in-place* shifts...
    - However, complexity increases (more swaps needed)
- Sequential accesses, good *cache* usage
- Integration with Insertion Sort (Python, Java7)

---

# Complexity Classes

---

![](http://fondinfo.github.io/images/comp/orders.svg) `$n$`: instance size
# 💡️ Complexity Classes

- *Constant*: number of operations does not depend on `$n$`
- *Sub-linear*: `$n^k, k<1$` <br> Or `$\log n$`, binary search
- *Linear*: number of operations `$\propto n$`, linear search
- *Super-linear*: `$n \log n$`, merge sort
- *Polynomial*: `$n^k, k \geq 2$`, insertion sort <br> 
- **Efficient algorithm**: up to polynomial class
- **Tractable problem**: `$\exists$` efficient algorithm

---

![](http://fondinfo.github.io/images/comp/orders.svg)
# 💡️ Exponential Complexity

- *Exponential*: `$k^n$`
    - E.g., listing subsets, perfect chess strategy
- *Super-exponential*: `$n!$`, `$n^n$`, …
    - E.g., listing permutations
- **Intractable problems**
    - $\nexists$ efficient algorithm
    - Non-exact/optimal solutions, heuristics
    - But local minima...

---

![](http://fondinfo.github.io/images/comp/knapsack.svg)
# ⭐ P and NP Problems

- **P** problems: $\exists$ *deterministic polynomial* algorithm
- **NP** problems: $\exists$ *non-deterministic polynomial* algorithm
    - On deterministic machines: no known polynomial algorithm for **finding** a solution...
    - But polynomial algorithm for **verifying** a solution
- NP example: *Knapsack*
    - $\exists$ configuration of items that achieves utility `≥V`, with weight `≤W`?
- *Languages of class P, or NP*: string `$x$` recognized in polynomial time with respect to `$|x|$` by *DTM*, or *NTM*

---

![](http://fondinfo.github.io/images/comp/challenges.jpg)
# ⭐ Millennium Problem

- We know that *`$P \subseteq NP$`* <br> (DTM: special case of NTM)
- **But it is not proven that `$P \neq NP$`, nor that `$P=NP$`**
    - [Millennium Prize Problems](https://en.wikipedia.org/wiki/Millennium_Prize_Problems): 1M$
    - If *`$P=NP$`*, solving a puzzle or verifying it: same complexity class
- *EXP class problems*: solved in exponential time by a DTM
    - We know that *`$NP \subseteq EXP$`* <br> (NTM: simulated by DTM in exponential time)
    - *`$P \subseteq NP \subseteq EXP$`*

---

![](http://fondinfo.github.io/images/comp/classes.svg)
# ⭐ NP-complete Problems

- Every NP problem can be reduced to an **NP-complete** problem with a *polynomial deterministic* algorithm
    - *Lower-bound* deterministic exponential for one of the NP-complete problems? *`$\Rightarrow P \neq NP$`*
    - Or, *solution* with a polynomial deterministic algorithm? *`$\Rightarrow P=NP$`*
- Example: *Knapsack*
- Example: *SAT*
    - Given a Boolean formula *CNF*, is it satisfiable?
    - `$\exists$` input configuration that yields true?
