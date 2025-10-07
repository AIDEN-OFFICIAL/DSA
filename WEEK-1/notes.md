# 1. What is Data structure and algorithm?

**Data Structure:**  
A data structure is a way to organize and store data so it can be accessed and modified efficiently.  
Examples: arrays, linked lists, stacks, queues, trees, graphs.

**Algorithm:**  
An algorithm is a step-by-step procedure to solve a specific problem.

---

# 2. Types of Data Structure

**Linear Data Structures**  
- Elements are arranged sequentially.  
- Contiguous memory allocation.  
- Easy traversal; insertion/deletion is slower.  
**Examples:** Array, Linked List, Stack, Queue  

**Non-Linear Data Structures**  
- Elements are **not arranged sequentially** (hierarchical or network form).  
- Non-contiguous memory allocation.  
- Traversal is more complex; insertion/deletion is easier.  
**Examples:** Tree, Graph, Hash Map, Trie  

---

# 3. Difference between Static and Dynamic DS

**Static:**  
- Fixed size  
- Memory allocated at **compile time**

**Dynamic:**  
- Grows dynamically  
- Memory allocated at **runtime**

---

# 4. Basics of Memory Allocation and Memory Leak

**Memory Allocation**  
It’s how a program reserves space in **RAM** to store data while it runs.  
1. **Static (Compile-time) Allocation**  
2. **Dynamic (Run-time) Allocation**

**Memory Leak**  
Happens when you allocate memory dynamically but never free it — memory stays occupied even when not needed.

### In JavaScript, memory leaks can be caused by:
- Global variables  
- Forgotten timers and intervals  
- Event listeners not removed  
- Closures holding references  
- Detached DOM elements  

**Prevent Memory Leaks by:**  
- Using `let` / `const` (avoid globals)  
- Using `WeakSet` and `WeakMap`  
- Clearing intervals and timeouts  
- Removing event listeners  
- Avoiding unnecessary closures  

---

# 5. Asymptotic Analysis (Big-O Notation)

**Asymptotic Analysis**  
A way to analyze an algorithm’s efficiency as input size increases.

| Big-O       | Name          | Example                    | Meaning                          |
|--------------|---------------|-----------------------------|-----------------------------------|
| **O(1)**     | Constant      | Accessing an array element  | Time doesn’t grow with input      |
| **O(log n)** | Logarithmic   | Binary search              | Grows slowly                      |
| **O(n)**     | Linear        | Loop through array         | Grows directly with input         |
| **O(n log n)** | Linearithmic | Merge sort, quicksort (avg) | Common in efficient sorts         |
| **O(n²)**    | Quadratic     | Nested loops               | Slower for large input            |
| **O(2ⁿ)**    | Exponential   | Recursive Fibonacci        | Very slow                         |
| **O(n!)**    | Factorial     | Permutation generation     | Extremely slow                    |

# 6. Learn the Concepts of Array

## 🧠 What is an Array?

An **Array** is a collection of elements stored at **contiguous memory locations**, allowing efficient access using **index numbers**.

It stores **multiple values of the same data type** under a single variable name.

Example (in JavaScript):
```js
let numbers = [10, 20, 30, 40];
```
## Types of Arrays?
1. Homogenous Array
2. Heterogenous Array
3. 1-Dimensional Array
4. Multi-Dimentional Array
5. Jagged Array
6. Dynamic Array
7. Sparse Array
8. Associate Array

### Homogenous Array
- Contains elements of the **Same Data Type**
- ex:C,C++,Java
### Heterogenous Array
- Contains elements of **Different data types**
- Allowed in Dynamically typed languages like JavaScript or Python
### 1-Dimentional Array
-Array with ony 1 dimention
### Multi-Dimentional Array
- Array of arrays (matrix)
- Each elemnts can be another array
- ex: 2D array , 3D array
### Jagged Array
- A multi dimentional array where inner array have different lengths
- ex:[[1,2,3],[3],[3,4,5,6]],
### Dynamic Array
- Arrays that can grow or shrink
- ex:arr.push(),arr.shift()
### Sparse Array
- array with many undefined or empy elements
- used for memory optimizations
- ex: [1,2,undefined, ,5]
### Associative Array:
- Uses key-value pairs instead of numeric indexes.
- ex: Js objects   person = { name: "Aiden", age: 21}

## Array Operations:
- Travesal: use for loops
- Insertion: arr.push()
- Deletion: arr.pop()
- Search: arr.indexOf(3)
- Update: arr[0]=10

# Search
## 🔍 Linear Search
**complexity: O(n)**
## 🧠 Concept
Li3near Search is the simplest searching algorithm.  
It checks **each element one by one** until the target element is found or the array ends.

---

### ⚙️ Approach / Steps
1. Start from the first element of the array.  
2. Compare each element with the target value.  
3. If a match is found → return its index.  
4. If not found after the last element → return “Not Found”.

---

### 💻 Example Code (JavaScript)
```js
function linearSearch(arr, target) {
  for (let i = 0; i < arr.length; i++) {
    if (arr[i] === target) {
      return `Found at index ${i}`;
    }
  }
  return 'Not Found';
}

let arr = [1, 2, 3, 4, 6, 7, 8, 9, 10, 5, 6, 7, 3, 2];
console.log(linearSearch(arr, 5));
```
## 🔍 Binary Search
**Complexity: O(log n)**
### 🧠 Concept
Binary Search is an efficient algorithm for finding an element in a **sorted array**.  
It repeatedly **divides the search interval in half**, comparing the middle element with the target.

If the target equals the middle element → found.  
If smaller → search the left half.  
If larger → search the right half.

---

### ⚙️ Approach / Steps
1. Start with two pointers: `start = 0`, `end = arr.length - 1`.  
2. Find the middle index: `mid = Math.floor((start + end) / 2)`.  
3. Compare:
   - If `arr[mid] === target` → Found  
   - If `arr[mid] > target` → Move left (`end = mid - 1`)  
   - If `arr[mid] < target` → Move right (`start = mid + 1`)  
4. Repeat until start > end.

---

## 💻 Example Code

#### ✅ Iterative Approach
```js
function binarySearch(arr, target) {
  let start = 0;
  let end = arr.length - 1;

  while (start <= end) {
    let mid = Math.floor((start + end) / 2);

    if (arr[mid] === target) {
      return `Element found at index ${mid}`;
    } else if (arr[mid] > target) {
      end = mid - 1;
    } else {
      start = mid + 1;
    }
  }
  return "Not found";
}

let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
console.log(binarySearch(arr, 7));

```
#### ✅ Recursive Approach

```js
function binaryRecursive(arr, target, start = 0, end = arr.length - 1) {
  if (start > end) return "Not found";

  let mid = Math.floor((start + end) / 2);

  if (arr[mid] === target) return `Element found at index ${mid}`;
  if (arr[mid] > target) return binaryRecursive(arr, target, start, mid - 1);
  return binaryRecursive(arr, target, mid + 1, end);
}

let arr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
console.log(binaryRecursive(arr, 7));
```
# Sort
## 🧩 Selection Sort
**Complexity: O(n²)**
### 🧠 Concept
Selection Sort is a simple **comparison-based sorting algorithm**.  
It repeatedly selects the **smallest (or largest)** element from the unsorted portion of the array and places it in its correct position.

---

### ⚙️ Approach / Steps
1. Loop through the array.  
2. Assume the current index `i` is the smallest.  
3. Compare this element with all elements after it (`j = i + 1`).  
4. If a smaller element is found, update the minimum index.  
5. Swap the minimum element with the element at index `i`.  
6. Repeat until the array is sorted.

---

## 💻 Example Code

### ✅ Basic Implementation
```js
let ar=[10,20,35,6,8,27,11,3]
function selection(arr){
    for(let i = 0 ; i <arr.length;i++){
    for(let j = i+1 ; j <arr.length;j++){
    if(arr[i]>arr[j]){
        let temp = arr[i]
        arr[i]=arr[j]
        arr[j]=temp
    }
    }
    }
    return arr
}
ar=selection(ar)
console.log(ar)
```
## 🌊 Bubble Sort
**Complexity: O(n²)**

### 🧠 Concept
Bubble Sort repeatedly compares **adjacent elements** and swaps them if they’re in the wrong order.  
With each pass, the largest element “bubbles up” to its correct position.

---

### ⚙️ Approach / Steps
1. Compare each pair of adjacent elements.  
2. Swap them if they are in the wrong order.  
3. Repeat passes until no swaps are needed (array is sorted).  
4. Can use a `swap` flag to stop early when sorted (optimization).

---

### 💻 Example Code (JavaScript)
```js
function bubbleSort(arr) {
  let swapped;
  do {
    swapped = false;
    for (let i = 0; i < arr.length - 1; i++) {
      if (arr[i] > arr[i + 1]) {
        [arr[i], arr[i + 1]] = [arr[i + 1], arr[i]];
        swapped = true;
      }
    }
  } while (swapped);
  return arr;
}

let arr = [10, 20, 35, 6, 8, 27, 11, 3];
console.log(bubbleSort(arr));
```
## 🧩 Insertion Sort
**Complexity: O(n²)**
### 🧠 Concept
Insertion Sort builds the sorted array **one element at a time** by taking each element and inserting it into its correct position among the previously sorted elements.

---

### ⚙️ Approach / Steps
1. Start from the second element (index 1).  
2. Compare it with elements to its left.  
3. Shift all elements larger than it to the right.  
4. Insert the current element into the correct position.  
5. Repeat until the array is sorted.

---
10,20,2
### 💻 Example Code (JavaScript)
```js
function insertionSort(arr) {
  for (let i = 1; i < arr.length; i++) {
    let current = arr[i];
    let j = i - 1;

    while (j >= 0 && arr[j] > current) {
      arr[j + 1] = arr[j];
      j--;
    }

    arr[j + 1] = current;
  }
  return arr;
}

let arr = [10, 20, 35, 6, 8, 27, 11, 3];
console.log(insertionSort(arr));
```
## ⚡ Merge Sort
**Complexity: O(n log n)**
### 🧠 Concept
Merge Sort is a **divide and conquer** algorithm.  
It divides the array into halves, sorts each half, and then merges them back together in sorted order.

---

### ⚙️ Approach / Steps
1. **Divide** the array into two halves until each subarray has one element.  
2. **Conquer** by merging sorted halves back into one sorted array.  
3. **Repeat recursively** until the entire array is sorted.

---

### 💻 Example Code (JavaScript)
```js
function mergeSort(arr) {
  if (arr.length < 2) return arr; // base case

  let mid = Math.floor(arr.length / 2);
  let left = arr.slice(0, mid);
  let right = arr.slice(mid);

  return mergeArrays(mergeSort(left), mergeSort(right));
}

function mergeArrays(left, right) {
  let sorted = [];

  while (left.length && right.length) {
    if (left[0] < right[0]) sorted.push(left.shift());
    else sorted.push(right.shift());
  }

  return [...sorted, ...left, ...right];
}

let arr = [10, 20, 35, 6, 8, 27, 11, 3];
console.log(mergeSort(arr));
```
## ⚡ Quick Sort
**Complexity: O(n log n)**
### 🧠 Concept
Quick Sort is a **divide and conquer** algorithm that:
- Picks a **pivot** element.
- Splits the array into two halves:
  - Left → elements **≤ pivot**
  - Right → elements **> pivot**
- Recursively sorts both halves, then merges them.

---

### ⚙️ Approach / Steps
1. Select a pivot (commonly first, last, or middle element).  
2. Partition the array:
   - If element ≤ pivot → move to left.
   - Else → move to right.
3. Recursively apply the process on left and right arrays.  
4. Combine the results: `[...sortedLeft, pivot, ...sortedRight]`.

---

### 💻 Example Code (JavaScript)
```js
function quickSort(arr) {
  if (arr.length < 2) return arr;

  let pivot = arr[0];
  let left = [];
  let right = [];

  for (let i = 1; i < arr.length; i++) {
    if (pivot < arr[i]) right.push(arr[i]);
    else left.push(arr[i]);
  }

  return [...quickSort(left), pivot, ...quickSort(right)];
}

let arr = [10, 20, 35, 6, 8, 27, 11, 3];
console.log(quickSort(arr));
```


### Inplace Sorting:
Sorting is done without using Extra space, sorts within the array
### Stable:  
Equal elements preserve their relative order after sorting

## Overview of Sorts
| Algorithm          | Best Case  | Average Case | Worst Case | Space Complexity | Stable | In-Place | Description                                                                                                                             |
| ------------------ | ---------- | ------------ | ---------- | ---------------- | ------ | -------- | --------------------------------------------------------------------------------------------------------------------------------------- |
| **Bubble Sort**    | O(n)       | O(n²)        | O(n²)      | O(1)             | ✅      | ✅        | Repeatedly swaps adjacent elements if they’re in the wrong order. Simple but inefficient.                                               |
| **Selection Sort** | O(n²)      | O(n²)        | O(n²)      | O(1)             | ❌      | ✅        | Selects the smallest element each pass and places it at the front. Few swaps but always O(n²).                                          |
| **Insertion Sort** | O(n)       | O(n²)        | O(n²)      | O(1)             | ✅      | ✅        | Builds the sorted array one element at a time by inserting into the correct position. Very efficient for small or nearly sorted arrays. |
| **Merge Sort**     | O(n log n) | O(n log n)   | O(n log n) | O(n)             | ✅      | ❌        | Divide and conquer algorithm that splits and merges arrays. Stable and predictable, but uses extra space.                               |
| **Quick Sort**     | O(n log n) | O(n log n)   | O(n²)      | O(log n)         | ❌      | ✅        | Divide and conquer algorithm using a pivot. Fastest in practice with good pivot selection.                                              |
| **Heap Sort**      | O(n log n) | O(n log n)   | O(n log n) | O(1)             | ❌      | ✅        | Uses a binary heap to repeatedly extract the max (or min). In-place but not stable.                                                     |


