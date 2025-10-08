# 🧠 Linked List – Complete Notes

A **Linked List** is a linear data structure where elements (nodes) are stored non-contiguously in memory.  
Each node points to the next, forming a chain-like structure.

Each **Node** generally contains:
- **Data** – value to store  
- **Pointer(s)** – reference(s) to next (and optionally previous) node(s)

---

## 🪢 Singly Linked List

### ⚙️ Approach / Steps
1. Each node has two parts — `data` and `next`.  
2. `head` points to the first node of the list.  
3. New nodes can be inserted at the **beginning**, **end**, or **specific position**.  
4. Deletion can occur at any position, adjusting `next` pointers accordingly.  
5. Traversal continues until the node’s `next` becomes `null`.

---

### ⚙️ Use Case
Used in stacks, queues, and basic data sequence implementations.

---

### 💻 Example Code (JavaScript)
```js
// Node Creation
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
  }
}

// Linked List Class
class LinkedList {
  constructor() {
    this.head = null;
  }

  isEmpty() {
    return this.head === null;
  }

  // Insert at beginning
  insertAtBeginning(data) {
    let node = new Node(data);
    node.next = this.head;
    this.head = node;
  }

  // Insert at end
  append(data) {
    let node = new Node(data);
    if (this.isEmpty()) {
      this.head = node;
      return;
    }
    let curr = this.head;
    while (curr.next) curr = curr.next;
    curr.next = node;
  }

  // Delete from beginning
  deleteBeginning() {
    if (this.isEmpty()) return;
    this.head = this.head.next;
  }

  // Reverse the list
  reverse() {
    let prev = null, curr = this.head;
    while (curr) {
      let next = curr.next;
      curr.next = prev;
      prev = curr;
      curr = next;
    }
    this.head = prev;
  }

  // Print the list
  print() {
    let curr = this.head, result = "";
    while (curr) {
      result += `${curr.data} -> `;
      curr = curr.next;
    }
    console.log(result + "null");
  }
}

// Example Usage
let list = new LinkedList();
list.insertAtBeginning(3);
list.insertAtBeginning(2);
list.append(5);
list.print(); // 2 -> 3 -> 5 -> null
list.reverse();
list.print(); // 5 -> 3 -> 2 -> null
```

---

## ⚙️ Time & Space Complexity – Singly Linked List

| Operation | Best Case | Average Case | Worst Case | Space Complexity |
|------------|------------|---------------|--------------|------------------|
| **Insertion (at head)** | O(1) | O(1) | O(1) | O(n) |
| **Insertion (at end)** | O(1) (if tail known) | O(n) | O(n) | O(n) |
| **Deletion (head)** | O(1) | O(1) | O(1) | O(n) |
| **Deletion (tail)** | O(n) | O(n) | O(n) | O(n) |
| **Search** | O(n) | O(n) | O(n) | O(n) |
| **Traversal** | O(n) | O(n) | O(n) | O(n) |

---

## 🧩 Doubly Linked List (DLL) – Documentation

A **Doubly Linked List** is a linear data structure where each node contains three parts:
1. `data` – the value stored in the node  
2. `prev` – a pointer/reference to the previous node  
3. `next` – a pointer/reference to the next node  

Unlike a **Singly Linked List**, a DLL allows traversal in **both directions**, making insertion and deletion operations more efficient at both ends.

---

### ⚙️ Use Case
Used in browser history (forward/back navigation), LRU caches, and editors (undo/redo).

---

### 💻 Example Code (JavaScript)
```js
class Node {
  constructor(data) {
    this.data = data
    this.prev = null
    this.next = null
  }
}
class DoublyLinkedList {
  constructor() {
    this.head = null
    this.tail = null
  }

  // Insert at the end
  append(data) {
    const newNode = new Node(data)
    if (!this.head) {
      this.head = this.tail = newNode
      return
    }
    this.tail.next = newNode
    newNode.prev = this.tail
    this.tail = newNode
  }

  // Insert at the beginning
  prepend(data) {
    const newNode = new Node(data)
    if (!this.head) {
      this.head = this.tail = newNode
      return
    }
    newNode.next = this.head
    this.head.prev = newNode
    this.head = newNode
  }

  // Delete a specific value
  delete(data) {
    if (!this.head) return null
    let current = this.head

    while (current) {
      if (current.data === data) {
        if (current.prev) current.prev.next = current.next
        else this.head = current.next

        if (current.next) current.next.prev = current.prev
        else this.tail = current.prev

        return
      }
      current = current.next
    }
  }

  // Traverse forward
  traverseForward() {
    let current = this.head
    const result = []
    while (current) {
      result.push(current.data)
      current = current.next
    }
    return result
  }

  // Traverse backward
  traverseBackward() {
    let current = this.tail
    const result = []
    while (current) {
      result.push(current.data)
      current = current.prev
    }
    return result
  }
}
const dll = new DoublyLinkedList()
dll.append(10)
dll.append(20)
dll.append(30)
dll.prepend(5)
dll.delete(20)

console.log("Forward:", dll.traverseForward())   // [5, 10, 30]
console.log("Backward:", dll.traverseBackward()) // [30, 10, 5]
```

---

## ⚙️ Time & Space Complexity – Doubly Linked List

| Operation | Best Case | Average Case | Worst Case | Space Complexity |
|------------|------------|---------------|--------------|------------------|
| **Insertion (at head/tail)** | O(1) | O(1) | O(1) | O(n) |
| **Insertion (at middle/position)** | O(1)* | O(n) | O(n) | O(n) |
| **Deletion (head/tail)** | O(1) | O(1) | O(1) | O(n) |
| **Deletion (middle/position)** | O(1)* | O(n) | O(n) | O(n) |
| **Search (by value)** | O(n) | O(n) | O(n) | O(n) |
| **Traversal (forward/backward)** | O(n) | O(n) | O(n) | O(n) |
| **Reverse Traversal** | O(n) | O(n) | O(n) | O(n) |

\*If node reference is already known.

---

✅ **Notes:**
- Insertion and deletion are **O(1)** when you already have a direct node reference.  
- Searching or inserting at a specific position requires **O(n)** traversal.  
- Overall space complexity remains **O(n)** due to the extra `prev` pointer in each node.

---

## 🔁 Circular Linked List (CLL)

### 🧠 Concept
A **Circular Linked List** is a variation of a linked list where:
- The **last node points back to the first node**, forming a continuous circle.
- It can be **Singly Circular** (last node points to head) or **Doubly Circular** (last node’s `next` points to head, and head’s `prev` points to the last node).

This structure allows **continuous traversal** — you can start at any node and keep moving without reaching `null`.

---

### ⚙️ Use Case
Used in task scheduling, buffer management, and multiplayer games (turn rotation).

---

### ⚙️ Key Characteristics
- No `null` at the end of the list.  
- The traversal must include a **stopping condition** to avoid infinite loops.  
- Supports **insertion and deletion at both ends** efficiently.  
- Commonly used in **round-robin scheduling**, **buffer management**, and **data streaming systems**.

---

### 🧩 Advantages
- Every node can be reached from any other node.  
- Efficient for applications requiring **cyclic iteration**.  
- **Insertion at the beginning or end** is simple (O(1)) when tail reference is maintained.

---

### ⚠️ Disadvantages
- More complex to handle than a standard singly linked list.  
- Traversal requires careful handling to avoid **infinite loops**.  
- Debugging is slightly harder since there’s no `null` to mark the end.

---

### ⏱️ Time & Space Complexity

| Operation | Time Complexity | Space Complexity |
|------------|----------------|------------------|
| **Insertion (head/tail)** | O(1) | O(n) |
| **Insertion (middle)** | O(n) | O(n) |
| **Deletion (head/tail)** | O(1) | O(n) |
| **Deletion (middle)** | O(n) | O(n) |
| **Traversal/Search** | O(n) | O(n) |

---

✅ **Notes:**
- Maintain a **tail pointer** to achieve O(1) insertion at both ends.  
- Traversal typically uses a **`do-while` loop** since the head is re-visited.  
- Often used when data needs to be **cycled repeatedly** (e.g., playlists, CPU scheduling).

---

## 🧩 Summary Comparison Table

| Type | Pointer Direction | Circular | Traversal | Memory | Use Cases |
|------|-------------------|-----------|------------|----------|-----------|
| **Singly Linked List** | One-way (Next) | ❌ | Forward only | Low | Stacks, queues |
| **Doubly Linked List** | Two-way (Next & Prev) | ❌ | Forward & backward | Medium | Undo/redo, LRU cache |
| **Circular Singly** | One-way | ✅ | Forward only (continuous) | Low | Round-robin, buffer |
| **Circular Doubly** | Two-way | ✅ | Forward & backward (continuous) | High | Playlists, schedulers |

---

✅ **In Short:**
- Use **Singly Linked List (SLL)** for simple one-directional traversal.  
- Use **Doubly Linked List (DLL)** when you need backward movement.  
- Use **Circular Linked List (CLL)** when you need continuous looping or scheduling behavior.
