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
