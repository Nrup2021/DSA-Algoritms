<div align="center">

# 🧠 DSA & Algorithms

### A visual, real-world guide to understanding Data Structures and Algorithms

**Understand where data lives. Understand how we use it. Connect every concept to real life.**

---

</div>

## 🗺️ Your Learning Map

| 🧱 Data Structures — *Where and how we store data* | ⚙️ Algorithms — *How we use stored data* |
| :--- | :--- |
| Linked List · Stack · Queue | Searching · Sorting |
| Hash Table · Hash Map · Set | Recursion · Backtracking |
| Tree · BST · AVL · Red-Black · Trie | DFS · BFS · Dijkstra's Algorithm |
| Graphs: Undirected · Directed · Weighted | Greedy · Divide and Conquer · Dynamic Programming |

> 💡 **The Big Idea:** A **Data Structure** is where and how we organize and store data. An **Algorithm** is the step-by-step procedure we use on that stored data to perform tasks and solve problems.

## 🎬 Reference

▶️ [Watch the reference video on YouTube](https://www.youtube.com/watch?v=RpLnQnurpLY)

---

# 🧱 Part 1 — Data Structures

## 1. Linear Data Structures

### 📚 Array / Array List

> **Think of:** Movie theater seats arranged with fixed numbers in a row.

- **Arranged linearly:** Elements are stored in contiguous memory positions.
- **Fast lookups, slow updates:** Fast to access by index ($O(1)$), but slower to insert or delete because elements must shift.
- **0-indexed:** Indexing begins at `0`.
- **Real-world example:** Storing student marks at designated roll-number indices for instant retrieval.

---

### 🔗 Linked List

> **Think of:** A treasure hunt game. Each clue or location holds the clue/address pointing to the next one.

- Nodes are connected sequentially; each node stores its value and a pointer/reference to the next node.
- **Easy insertions & deletions:** Simply re-point the references without shifting an entire collection.
- **Slower searching:** Must traverse sequentially from the head node, step-by-step, until reaching the target.

| Type | How it Works / Real-World Analogy |
| :--- | :--- |
| **Singly Linked List** | Traversal moves in one direction only (forward). |
| **Doubly Linked List** | Traversal moves in both directions (forward and backward). |
| **Circular Linked List** | The last node connects back to the first node (no start or end). *Example:* A music playlist set to repeat continuously. |

---

### 🍽️ Stack

> **Think of:** A stack of clean dishes at a buffet.

- **LIFO (Last In, First Out):** The last plate placed on top is the first plate taken off.
- **Core operations:**
  - **Push:** Add an item to the top.
  - **Pop:** Remove the top item.
- **Real-world example:** Browser back-button history (the last page visited is the first page returned to) or Undo/Redo in text editors.

```text
        ┌─────────┐
TOP  →  │  Dish 3 │  ← Last In (First to be removed)
        ├─────────┤
        │  Dish 2 │
        ├─────────┤
        │  Dish 1 │  ← First In
        └─────────┘

        POP removes from the TOP; PUSH adds to the TOP
```

---

### 🚶 Queue

> **Think of:** A line of customers submitting cheques at a bank counter, or print jobs queued for a printer.

- **FIFO (First In, First Out):** First person in line is the first person served.
- **Two ends:**
  - **Enqueue:** New items/customers join at the **REAR**.
  - **Dequeue:** Items/customers exit from the **FRONT** once served.
- *Standard linear queue note:* In simple array-based queues, freed space at the front cannot easily be reused unless shifted.

```text
ENQUEUE →  REAR  [ Person 3 ] [ Person 2 ] [ Person 1 ]  FRONT  → DEQUEUE
                         Last in                  First out
```

#### 🔄 Circular Queue
- The last position is connected directly back to the first position in a ring.
- Reuses freed memory slots at the front as soon as items leave.
- **Real-world example:** CPU Round-Robin task scheduling.

```text
        ┌──────────────────────┐
        ↓                      │
     [ 1 ] → [ 2 ] → [ 3 ] → [ 4 ]
        ↑                      ↓
        └──────────────────────┘
        Last connects back to first
```

#### ↔️ Double-Ended Queue (Deque)
- Elements can be inserted or deleted from **both** ends (Front and Rear).

#### 🚨 Priority Queue
> **Think of:** A hospital emergency room triage: a patient with a critical condition gets treated immediately, ahead of patients who arrived earlier.

- Served by **highest priority**, not by arrival order.
- **Real-world examples:** VIP / diplomatic motorcade entry at an event, or operating system process scheduling prioritizing critical tasks.
- **Implemented with a Heap (Pyramid structure):**
  - **Max-Heap:** Highest numerical value sits at the root/peak. *Example:* Ranking students where 100% is at the top.
  - **Min-Heap:** Lowest numerical value sits at the root/peak. *Example:* A 100-meter race where the lowest time wins the top spot.

---

## 2. 🗝️ Hash Table, Hash Map & Set

### The Problem: Finding a Contact
Arrays, Linked Lists, and Queues rely on indices or linear traversal. But what if you don't know an index or position?
- **Example:** Searching for a specific friend's number inside a phonebook of 1,000+ contacts. Scanning one by one is too slow; you need direct lookup.

### Hash Table
> A **Hash Table** passes a key through a **Hash Function** to compute an exact memory index where the data is stored.

### Hash Map
> A **Hash Map** is a key-value data structure built on top of hashing principles.

- **Key-Value Pairs:** Each entry has a unique key (e.g., phone number or username) mapped to a value (e.g., contact profile).
- **Direct Lookup:** The hash function turns the key into an exact memory address, enabling ultra-fast average $O(1)$ retrieval.
- **Keys vs. Values:** Keys must be **unique**; values can contain duplicates.

```text
KEY                         VALUE
"9876543210"  ───────────→  Contact Details
                              Name + Details
                                  │
                                  ▼
                            Hash Function
                                  │
                                  ▼
                        Specific Memory Address
```

### Set
- A collection that stores **unique elements only**.
- Automatically rejects duplicate values.

---

# 🌳 Part 2 — Hierarchical Data Structures

Most real-world data naturally follows a hierarchical structure rather than a flat linear list.

## 3. Tree

> **Think of:** A family tree showing generations, or the folder hierarchy on your computer.

- Built around a **Root** (top-level node) and **Leaves** (end nodes with no children).
- **Real-world example:** File explorer filesystem (`C:/Folders/Subfolders/Files`).

```text
                 ROOT
                   │
             ┌─────┴─────┐
          Parent       Parent
           /  \         /  \
        Leaf  Leaf    Leaf  Leaf
```

---

## 4. Binary Search Tree (BST)

- Each parent node has at most **two children** (Left and Right).
- **The BST Rule:**
  - Values **smaller** than the parent go to the **Left**.
  - Values **larger** than the parent go to the **Right**.
- *Example (Numbers 1 to 100):* If `50` is the root, all numbers $< 50$ go left, and all numbers $> 50$ go right.
- **The Problem:** If data is inserted in pre-sorted order (`1, 2, 3, 4, 5`), the tree becomes a skewed straight line (acting like a slow linked list).

```text
                 50
               /    \
             25      75
            /  \    /  \
           10  40  60  90

      Lower values ← 50 → Higher values
```

---

## 5. ⚖️ Balanced Trees

### AVL Tree (Adelson-Velsky and Landis)
- If one side of a tree becomes too deep or skewed, an AVL tree performs **rotations** to rebalance it evenly.
- *Example:* Inserting sorted values `1 → 2 → 3 → 4 → 5` normally skews right. An AVL tree rotates nodes so `3` becomes the root, keeping both sides balanced.
- Guarantees $O(\log n)$ search, insert, and delete operations at all times.
- **Real-world example:** Large-scale database indexing engines.

```text
Before Balancing: Skewed Tree        After Balancing: AVL Rotations

        1                                    3
         \                                 /   \
          2                               2     4
           \                             /       \
            3                           1         5
             \
              4
               \
                5
```

### Red-Black Tree
- A self-balancing binary search tree where every node is colored either **Red** or **Black**.
- Follows strict color and height rules to ensure the tree remains approximately balanced with fewer rotations during updates than AVL trees.

---

## 6. 🔤 Trie (Prefix Tree)

- Name originates from re**TRIE**val.
- Stores characters sequentially along paths so words sharing common prefixes share the same branches.
- **Real-world examples:** Search engine autocomplete ("How to..."), dictionary spell checkers, predictive text.

```text
              (root)
                │
                c
                │
                a
              /   \
             t     r
             │     │
            "cat" "car"

      Shared prefix ("ca-") organizes related words efficiently
```

---

# 🕸️ Part 3 — Complex Data Structures

## 7. Graph

> **A Graph is the most flexible data structure: it models arbitrary networks with no strict hierarchy or ordering rules.**

### Real-World Examples
- **Social Networks:** Facebook friends, LinkedIn connections.
- **Navigation:** Google Maps, road and airline networks.
- **Web Pages:** Hyperlinks connecting websites across the internet.

### Fundamentals of a Graph
- **Vertex (Node):** An individual point or entity.
  - On Facebook: Each person is a Vertex.
  - On Google Maps: Each city or intersection is a Vertex.
- **Edge:** The connection or relationship between two vertices.
  - On Facebook: Friendship/relationship is an Edge.
  - On Google Maps: The road/pathway between two cities is an Edge.

```text
Undirected Graph                   Directed Graph (One-way)

     (A) ───── (B)                     (A) ─────→ (B)
      │          │
      │          │
     (C) ───── (D)                     Unidirectional connection
```

### Graph Types

| Type | Meaning & Real-World Example |
| :--- | :--- |
| **Undirected Graph** | Connections are two-way. If A is friends with B on Facebook, B is also friends with A. |
| **Directed Graph (Digraph)** | Connections are one-way. On Twitter (X) or Instagram, you can follow someone without them following you back. |
| **Weighted Graph** | Each edge carries a cost, weight, distance, or time.<br>• *Example:* Google Maps or Uber routing.<br>• Ahmedabad → Vadodara: `100 km, 2 hrs`<br>• Ahmedabad → Mumbai: `500 km, 10 hrs` |

---

# ⚙️ Part 4 — Algorithms

> **Algorithms define how we process, search, and transform stored data to solve real-world problems.**

## 8. 🔎 Searching

### Linear Search
- Checks elements sequentially, one by one, from start to finish until the target is found.
- **Use case:** Unsorted lists or small collections.
- **Drawback:** Slow on large datasets ($O(n)$ time).

```text
Search for 7:   [ 2 ] → [ 4 ] → [ 7 ] → [ 9 ]
                Check   Check   FOUND ✓
```

### Binary Search
- Efficiently finds a target by repeatedly dividing a **sorted** list in half.
- Checks the middle element: if the target is smaller, search the left half; if larger, search the right half.
- **Prerequisite:** The data **must be sorted** beforehand.
- **Real-world example:** Looking up a name in a physical dictionary or telephone directory.

```text
Sorted Data: [ 10,  20,  30,  40,  50,  60,  70 ]
                              │
                        Check Middle (40)
                   ┌──────────┴──────────┐
              Search Left            Search Right
             (if target < 40)       (if target > 40)
```

---

## 9. 🔃 Sorting

### Bubble Sort — *Compare adjacent pairs and bubble up the largest*
- Compares adjacent elements starting from the beginning.
- If the left element is greater than the right element, it swaps them.
- The largest unsorted value "bubbles up" to the end of the array on each pass.
- Repeat until the entire list is sorted.
- **Tradeoff:** Intuitive and easy to grasp, but inefficient for large datasets ($O(n^2)$).

```text
[ 5, 2, 4, 1 ]  →  [ 2, 5, 4, 1 ]  →  [ 2, 4, 5, 1 ]  →  [ 2, 4, 1, 5 ]
     Adjacent elements compared and swapped; largest value bubbles to the end
```

### Selection Sort — *Find the smallest remaining item first*
- Scans the unsorted portion of the list, identifies the smallest element, and swaps it into its final position at the front.
- Then finds the next smallest from the remainder and places it second.
- **Real-world example:** A teacher lining up students by height from shortest to tallest by repeatedly picking the shortest student remaining.

### Insertion Sort — *Insert each element into its sorted position*
- Takes elements one at a time and inserts each into its proper sorted place among previously considered elements.
- **Real-world example:** Sorting playing cards in your hand. If you hold `[2, 5, 9]` and draw a `7`, you slide `7` into place between `5` and `9`.

```text
Already sorted hand:   [ 2 ] [ 5 ] [ 9 ]
Draw new card:                     [ 7 ]
Insert into position:  [ 2 ] [ 5 ] [ 7 ] [ 9 ]
```

### Merge Sort — *Divide into halves, sort, and merge*
- **Divide and Conquer strategy:** Recursively divides a list into halves until individual single-element lists remain.
- Then repeatedly merges adjacent halves in sorted ascending order up the chain.
- Highly efficient and consistent ($O(n \log n)$); ideal for sorting large-scale datasets (millions of records).

```text
                 [ 8, 3, 6, 2 ]
                    /       \
                [ 8, 3 ]   [ 6, 2 ]
                 /   \       /   \
                [8]  [3]   [6]  [2]
                 \   /       \   /
                [ 3, 8 ]   [ 2, 6 ]
                    \       /
                 [ 2, 3, 6, 8 ]
```

### Quick Sort — *Partition around a pivot*
- Selects a benchmark element called a **Pivot** (or "leader").
- Partitions the remaining items: all elements smaller than the pivot move to the left; all elements larger move to the right.
- Recursively applies the same process to both the left and right sub-arrays.

```text
                     Pivot: 5
                     /      \
             Smaller          Larger
             [ 2, 3 ]         [ 7, 9 ]
       (Recursively repeat pivot partitioning on each half)
```

> 📌 **Industry Note:** Most standard library sort algorithms across modern programming languages (such as Python's Timsort or C++/Java's Introsort/Dual-Pivot Quicksort) are built on combinations of Merge Sort and Quick Sort principles.

---

## 10. 🔁 Recursion

- **Definition:** A process or function that calls itself to solve smaller sub-problems.
- **Classic Math Example:** Factorial computation:
  $$5! = 5 \times 4 \times 3 \times 2 \times 1 = 120$$
- **Real-World Analogy:** Standing between two parallel mirrors in a salon or dressing room, producing an endless chain of reflections.
- **Base Case (Stopping Condition):**
  - Every recursive function **must have a base case** to stop calling itself.
  - Without a base case, recursion runs infinitely and triggers a **Stack Overflow** crash.
- **Backtracking Application:** Recursion powers backtracking. You explore a candidate path step-by-step; if you hit an invalid state, you backtrack to the previous decision point and try an alternative.
  - *Examples:* Solving a **Sudoku** grid (testing digits 1–9 per cell), navigating a maze, or evaluating moves in **Chess**.

```text
factorial(5)
   ↓
5 × factorial(4)
       ↓
     4 × factorial(3)
             ↓
           3 × factorial(2)
                   ↓
                 2 × factorial(1)
                         ↓
                    Base Case (Returns 1)
```

---

## 11. 🧭 Traversing Trees and Graphs

### Depth-First Search (DFS)
- Plunges as deep as possible down one branch until hitting a dead end or leaf, then backtracks to explore unexplored branches.
- **Analogy:** Solving a maze by picking one hallway and walking until you hit a wall before turning back.

```text
DFS: Explore deep first

        A
       / \
      B   C
     /
    D  ← Follows branch (A → B → D) to depth, then backtracks
```

### Breadth-First Search (BFS)
- Explores all immediate neighbors at the current depth before descending to nodes at the next depth level.
- **Analogy:** Dropping a pebble into water—ripples expand outward uniformly level by level.
- **Real-world example:** LinkedIn or Facebook network exploration: 1st-degree connections $\rightarrow$ 2nd-degree connections $\rightarrow$ "People You May Know".

```text
BFS: Explore level by level

        A          Level 0 (Root)
       / \
      B   C        Level 1 (Direct connections)
     / \   \
    D   E   F      Level 2 (Secondary connections)
```

### Dijkstra's Shortest Path Algorithm
- Finds the shortest or cheapest path from a starting node to destinations across a weighted graph.
- **Relaxation:** The process of continually updating a known distance with a newly discovered shorter or lower-cost route.
- **Data structure used:** Utilizes a **Min-Heap (Priority Queue)** to always extract the lowest-cost unvisited vertex efficiently.
- **Real-world example:** Google Maps or delivery dispatch algorithms calculating the fastest route between locations.

```text
       4          2
   (A) ───── (B) ───── (D)
    │                   ▲
  1 │                   │ 1
    └────── (C) ────────┘

Dijkstra's idea: Compare candidate route costs and iteratively relax to keep the cheapest path.
```

---

## 12. 🧩 Four Core Algorithm Philosophies

Almost all computer science algorithms stem from four fundamental problem-solving philosophies:

| Philosophy | Core Concept & Real-World Analogy |
| :--- | :--- |
| **Greedy** | Makes the best, most optimal choice available at the current moment without reconsidering past choices.<br>• *Analogy:* A cashier giving change using the largest denomination coin/bill available first. |
| **Divide and Conquer** | Breaks a large problem down into smaller independent sub-problems, solves them recursively, and combines their solutions.<br>• *Examples:* Merge Sort, Quick Sort, Binary Search. |
| **Dynamic Programming (DP)** | Breaks problems into overlapping sub-problems, solves each once, and stores (memoizes/caches) the results in memory to avoid redundant recomputation.<br>• *Analogy:* Taking notes while studying so you look up an answer instantly rather than recalculating it from scratch every time. |
| **Backtracking** | Systematically explores possible paths step-by-step; when a path hits a dead end or constraint violation, it steps back (undoes the last move) to try alternative paths.<br>• *Examples:* Solving Sudoku, N-Queens, and maze-solving algorithms. |

---

# 🚀 Quick Revision — Which Data Structure Should I Use?

| When you need to... | Consider... |
| :--- | :--- |
| Frequently insert or delete in the middle without shifting data | **Linked List** |
| Strictly control processing order (LIFO or FIFO) | **Stack** (LIFO) or **Queue** (FIFO) |
| Look up items with instant speed ($O(1)$) | **Hash Map / Hash Table** |
| Keep data ordered with logarithmic search time | **Binary Search Tree (BST) / Balanced Tree (AVL)** |
| Store and retrieve words or prefix matches (autocomplete) | **Trie** |
| Model networks, routes, and relationships | **Graph** |

---

## 🧠 One-Minute Memory Guide

- **Array / List** → Fixed numbered seats / instant index access ($O(1)$).
- **Linked List** → Treasure hunt / each node points to the next.
- **Stack** → Buffet plates / Last In, First Out (LIFO) / Push & Pop.
- **Queue** → Bank counter / First In, First Out (FIFO) / Enqueue & Dequeue.
- **Circular Queue** → Ring buffer / Round-Robin scheduling / reuses freed slots.
- **Double-Ended Queue (Deque)** → Insert and remove freely from both ends.
- **Priority Queue** → Hospital triage / highest priority served first / backed by Heaps.
- **Hash Map** → Phonebook lookup / unique keys mapped to values / instant access.
- **Set** → Collection of strictly unique items / automatic deduplication.
- **Tree** → Family tree or folder directory / hierarchical parent-child structure.
- **Binary Search Tree (BST)** → Left is smaller, right is larger.
- **AVL Tree** → Self-balancing BST using rotations to prevent skew.
- **Red-Black Tree** → Self-balancing BST using color tags (red/black) and rules.
- **Trie** → Prefix tree / autocomplete and dictionary spell check.
- **Graph** → Vertices (entities) and Edges (relationships) / social networks and maps.
- **Linear Search** → Scan one-by-one from the start / $O(n)$.
- **Binary Search** → Repeatedly halve sorted data / $O(\log n)$.
- **Bubble Sort** → Compare neighbors; largest values bubble to the top.
- **Selection Sort** → Repeatedly find and move the smallest remaining item to the front.
- **Insertion Sort** → Insert each incoming card into its sorted position.
- **Merge Sort** → Divide into halves, sort base pieces, and merge back together.
- **Quick Sort** → Pick a pivot; place smaller items left, larger items right, recurse.
- **Recursion** → A function calling itself; requires a base case to avoid stack overflow.
- **DFS** → Explore deep along one branch, then backtrack / maze exploration.
- **BFS** → Explore outward level-by-level / ripples in water / social network degrees.
- **Dijkstra's Algorithm** → Shortest path on weighted graphs using relaxation and Min-Heaps.
- **Greedy** → Take the immediately best option at every step.
- **Divide and Conquer** → Split into independent sub-problems and recombine.
- **Dynamic Programming** → Store sub-problem results to eliminate duplicate computation.
- **Backtracking** → Test a path; backtrack when hitting a dead end to try other options.

---

<div align="center">

### 🌟 Keep learning. Keep visualizing. Keep solving.

**Data Structures = how data is organized · Algorithms = how problems are solved**

</div>
