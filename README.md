# DSA Complete Guide

### What is Big-O Notation?  
Big-O Notation is a way to measure how well an algorithm performs as the input size (\( n \)) grows. It focuses on the **worst-case scenario**, which is the maximum number of steps an algorithm might take.

It answers questions like:  
- "If my input size doubles, will my algorithm take twice as long? Or will it grow much faster?"
- "Which algorithm is faster for large inputs?"

---

### Why Do We Use Big-O?  
When comparing two algorithms, Big-O tells us:  
1. **How fast the runtime grows as the input size increases.**  
2. **Which algorithm will perform better in the long run.**

---

### Common Big-O Complexity Classes  
These are the most common types of Big-O notations, sorted from fastest to slowest:

| Big-O       | Name                 | Example Use Case                         |
|-------------|----------------------|------------------------------------------|
| \( O(1) \)  | Constant Time        | Accessing an element in an array         |
| \( O(\log n) \) | Logarithmic Time | Binary Search                            |
| \( O(n) \)  | Linear Time          | Linear Search                            |
| \( O(n \log n) \) | Log-Linear Time | Merge Sort, Quick Sort (best case)       |
| \( O(n^2) \) | Quadratic Time      | Nested loops (e.g., Bubble Sort)         |
| \( O(2^n) \) | Exponential Time    | Recursive problems like the Fibonacci sequence |

---

### Examples of Big-O with Simple Algorithms  

#### 1. **Constant Time - \( O(1) \)**  
An algorithm that always takes the same amount of time, regardless of input size.  

```javascript
function getFirstElement(array) {
    return array[0]; // Accessing an element takes the same time
}

console.log(getFirstElement([10, 20, 30])); // Output: 10
```

Here, no matter how large the array is, it always takes **1 step** to get the first element.

---

#### 2. **Linear Time - \( O(n) \)**  
An algorithm where the time taken grows directly with the input size.

```javascript
function sumArray(array) {
    let sum = 0;
    for (let i = 0; i < array.length; i++) {
        sum += array[i]; // Loop runs once for each element
    }
    return sum;
}

console.log(sumArray([1, 2, 3, 4])); // Output: 10
```

If the array has 4 elements, the loop runs 4 times. If the array has 1,000 elements, it runs 1,000 times. Runtime grows **linearly** with \( n \).

---

#### 3. **Logarithmic Time - \( O(\log n) \)**  
An algorithm that reduces the problem size by half each step.

```javascript
function binarySearch(array, target) {
    let left = 0, right = array.length - 1;

    while (left <= right) {
        let mid = Math.floor((left + right) / 2);

        if (array[mid] === target) return mid; // Found the target
        else if (array[mid] < target) left = mid + 1; // Search the right half
        else right = mid - 1; // Search the left half
    }

    return -1; // Target not found
}

console.log(binarySearch([10, 20, 30, 40, 50], 30)); // Output: 2
```

In each step, the array size is halved. For 1,000 elements, it takes about 10 steps; for 1,000,000 elements, it takes about 20 steps. Runtime grows **logarithmically**.

---

#### 4. **Quadratic Time - \( O(n^2) \)**  
An algorithm with nested loops, where every element interacts with every other element.

```javascript
function printPairs(array) {
    for (let i = 0; i < array.length; i++) {
        for (let j = 0; j < array.length; j++) {
            console.log(`(${array[i]}, ${array[j]})`);
        }
    }
}

printPairs([1, 2, 3]);
```

If the array has 3 elements, it prints \( 3 \times 3 = 9 \) pairs. For 1,000 elements, it prints 1,000,000 pairs. Runtime grows **quadratically**.

---

### Visualizing Growth  

| Input Size (\( n \)) | \( O(1) \) | \( O(\log n) \) | \( O(n) \) | \( O(n^2) \) |
|-----------------------|------------|------------------|------------|--------------|
| 10                   | 1          | 3                | 10         | 100          |
| 100                  | 1          | 7                | 100        | 10,000       |
| 1,000                | 1          | 10               | 1,000      | 1,000,000    |

For large inputs, algorithms with lower Big-O complexities are far more efficient.

---

### Key Takeaways  
1. **Big-O describes the worst-case performance.**  
2. **Aim for algorithms with smaller growth rates**, like \( O(1) \), \( O(\log n) \), or \( O(n) \).  
3. **Understanding Big-O helps choose the right algorithm for the job!**

### What is Theta (\( \Theta \)) Notation?  
Theta (\( \Theta \)) notation is used to describe the **average-case performance** of an algorithm. It tells us how an algorithm typically behaves, instead of focusing only on the worst-case or best-case scenarios.

In simpler terms:  
- **Big-O Notation (\( O \))** gives the upper limit (worst-case).  
- **Omega Notation (\( \Omega \))** gives the lower limit (best-case).  
- **Theta Notation (\( \Theta \))** provides a **tight bound**: it shows that the actual runtime of an algorithm will always lie between the best-case and worst-case for large input sizes.

---

### Real-Life Analogy  
Imagine a train that takes **30 minutes on average** to travel from City A to City B.  
- Sometimes it might take longer (e.g., bad weather or delays).  
- Sometimes it might take less time (e.g., perfect conditions).  
- But generally, the train **averages around 30 minutes.**

Theta notation is like saying, “The journey will take around 30 minutes, give or take a little.”

---

### Theta (\( \Theta \)) Notation Explained  
If an algorithm’s runtime lies between \( c_1 \cdot f(n) \) and \( c_2 \cdot f(n) \) for large \( n \), it is \( \Theta(f(n)) \).  

\[
\Theta(f(n)) = \text{Lower bound: } c_1 \cdot f(n), \quad \text{Upper bound: } c_2 \cdot f(n)
\]

This means the algorithm **consistently scales** with \( f(n) \).

---

### Examples of Theta Notation

#### 1. **Linear Search (\( \Theta(n) \)):**  
In a linear search, you go through a list element by element to find a target.  

**Code Example:**
```javascript
function linearSearch(array, target) {
    for (let i = 0; i < array.length; i++) {
        if (array[i] === target) return i; // Found target
    }
    return -1; // Target not found
}
```

- If the target is the **first element**, it takes \( \Omega(1) \) (best-case).  
- If the target is the **last element** or missing, it takes \( O(n) \) (worst-case).  
- On **average**, the target is somewhere in the middle, so it takes \( \Theta(n) \).

---

#### 2. **Binary Search (\( \Theta(\log n) \)):**  
Binary search splits the list in half repeatedly until it finds the target.  

**Code Example:**
```javascript
function binarySearch(array, target) {
    let left = 0, right = array.length - 1;

    while (left <= right) {
        let mid = Math.floor((left + right) / 2);
        if (array[mid] === target) return mid;
        else if (array[mid] < target) left = mid + 1;
        else right = mid - 1;
    }

    return -1; // Target not found
}
```

- **Best-case:** \( \Omega(1) \) (target is in the middle).  
- **Worst-case:** \( O(\log n) \) (target is at the far end).  
- **Average-case:** \( \Theta(\log n) \), because you generally reduce the problem size by half at each step.

---

#### 3. **Bubble Sort (\( \Theta(n^2) \)):**  
Bubble sort compares every pair of elements repeatedly to sort a list.  

**Code Example:**
```javascript
function bubbleSort(array) {
    let n = array.length;
    for (let i = 0; i < n - 1; i++) {
        for (let j = 0; j < n - i - 1; j++) {
            if (array[j] > array[j + 1]) {
                [array[j], array[j + 1]] = [array[j + 1], array[j]]; // Swap
            }
        }
    }
    return array;
}
```

- **Best-case:** \( \Omega(n) \) (list is already sorted; single pass).  
- **Worst-case:** \( O(n^2) \) (list is completely reversed).  
- **Average-case:** \( \Theta(n^2) \), as comparisons occur for every pair of elements.

---

### Key Takeaways  
1. **Theta Notation Provides the Tight Bound:**  
   It tells us the average runtime of an algorithm.  
   - If runtime always grows as \( n^2 \), the algorithm is \( \Theta(n^2) \).  
   - If runtime always grows as \( \log n \), it’s \( \Theta(\log n) \).

2. **Why Use Theta Notation?**  
   It’s useful when you want a realistic measure of algorithm performance, rather than focusing only on extremes.

3. **Examples in Simple Terms:**  
   - **Linear Search:** \( \Theta(n) \) because, on average, you check half the elements.  
   - **Binary Search:** \( \Theta(\log n) \) because you repeatedly divide the search space.  
   - **Sorting Algorithms:**  
     - Merge Sort: \( \Theta(n \log n) \)  
     - Bubble Sort: \( \Theta(n^2) \)
