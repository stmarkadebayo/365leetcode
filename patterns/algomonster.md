# AlgoMonster Flowchart: Complete Guide to Solving LeetCode Problems

## Table of Contents
1. [Introduction](#introduction)
2. [How to Use This Guide](#how-to-use-this-guide)
3. [Algorithm Definitions (Endpoints)](#algorithm-definitions-endpoints)
4. [Flowchart Visualization](#flowchart-visualization)
5. [Decision Tree Structure](#decision-tree-structure)
6. [Runtime to Algorithm Mapping](#runtime-to-algorithm-mapping)
7. [Additional Resources](#additional-resources)
8. [How to Practice with This Guide](#how-to-practice-with-this-guide)
9. [Common Patterns and Their Indicators](#common-patterns-and-their-indicators)
10. [Tips for Effective Problem Solving](#tips-for-effective-problem-solving)

---

## Introduction

The AlgoMonster flowchart, developed by ex-Googlers and competitive programmers, is based on solving thousands of problems and identifying common patterns. Its purpose is to provide a structured method for approaching LeetCode problems systematically.

### What is it?

The AlgoMonster flowchart is a decision tree that guides you through solving LeetCode problems by asking a series of questions about the problem characteristics. Each question (represented as a yellow diamond) leads you closer to identifying the appropriate algorithm (represented as a purple box).

### How to Use It?

**Internal nodes (diamonds)** are decisions based on problem description. **Leaf nodes (purple boxes)** are the algorithms you would need to solve the problem. Traverse the tree from the root until you reach a leaf node (algorithm).

### Do I Memorize This?

**NO.** The flowchart is a tool and a reference to help you understand the patterns. As you work through problems using the flowchart, you will naturally get better at recognizing which algorithm to use. The goal is pattern recognition, not memorization.

---

## Algorithm Definitions (Endpoints)

This section defines all the algorithms (endpoints) you might reach when traversing the flowchart. Understanding these algorithms is crucial before using the flowchart effectively.

### 1. Depth-First Search (DFS)

**Definition**: DFS is a graph/tree traversal algorithm that explores as far as possible along each branch before backtracking. It uses a stack (either explicitly or via recursion) to keep track of nodes to visit.

**Key Characteristics**:
- Explores one path completely before moving to the next
- Uses recursion or an explicit stack
- Memory efficient for deep trees (O(h) where h is height)
- Can be used for: tree traversal, graph traversal, path finding, cycle detection

**When to Use**:
- Tree problems (preorder, inorder, postorder traversal)
- Graph problems (exploring all nodes, finding paths)
- Backtracking problems (exploring all possibilities)
- Problems requiring deep exploration before backtracking

**Time Complexity**: O(V + E) for graphs, O(n) for trees
**Space Complexity**: O(h) for trees (recursion stack), O(V) for graphs

---

### 2. Breadth-First Search (BFS)

**Definition**: BFS is a graph/tree traversal algorithm that explores all nodes at the current depth level before moving to nodes at the next depth level. It uses a queue to keep track of nodes to visit.

**Key Characteristics**:
- Explores level by level
- Uses a queue data structure
- Guarantees finding the shortest path in unweighted graphs
- Can be used for: level-order traversal, shortest path in unweighted graphs, finding minimum steps

**When to Use**:
- Finding shortest path in unweighted graphs
- Level-order tree traversal
- Problems requiring exploring all nodes at a distance k before distance k+1
- Finding minimum steps to reach a target

**Time Complexity**: O(V + E) for graphs, O(n) for trees
**Space Complexity**: O(w) where w is maximum width of tree/graph

---

### 3. Topological Sort

**Definition**: Topological sort is a linear ordering of vertices in a directed acyclic graph (DAG) such that for every directed edge (u, v), vertex u comes before v in the ordering.

**Key Characteristics**:
- Only works on Directed Acyclic Graphs (DAGs)
- Multiple valid orderings may exist
- Uses DFS or Kahn's algorithm (BFS-based)
- Can be used for: task scheduling, dependency resolution, course prerequisites

**When to Use**:
- Directed graph problems
- Problems with dependencies (A must happen before B)
- Course prerequisites
- Build order problems
- Detecting cycles in directed graphs (if topological sort fails, cycle exists)

**Time Complexity**: O(V + E)
**Space Complexity**: O(V)

---

### 4. Dijkstra's Algorithm

**Definition**: Dijkstra's algorithm finds the shortest path from a source vertex to all other vertices in a weighted graph with non-negative edge weights.

**Key Characteristics**:
- Works only with non-negative edge weights
- Uses a priority queue (min-heap)
- Greedy algorithm (always picks the closest unvisited vertex)
- Can be used for: shortest path in weighted graphs, network routing

**When to Use**:
- Weighted graph problems
- Finding shortest path with non-negative weights
- Single-source shortest path problems
- Problems where you need optimal path in weighted scenarios

**Time Complexity**: O((V + E) log V) with binary heap, O(V log V + E) with Fibonacci heap
**Space Complexity**: O(V)

---

### 5. Disjoint Set Union (DSU) / Union-Find

**Definition**: DSU is a data structure that efficiently tracks a partition of a set into disjoint subsets. It supports two operations: `find` (which subset an element belongs to) and `union` (merge two subsets).

**Key Characteristics**:
- Efficient for connectivity problems
- Uses path compression and union by rank optimizations
- Near-constant time operations (amortized)
- Can be used for: connected components, cycle detection in undirected graphs, Kruskal's MST algorithm

**When to Use**:
- Connectivity problems (are two nodes connected?)
- Finding connected components
- Cycle detection in undirected graphs
- Problems asking "how many groups/clusters?"
- Minimum Spanning Tree (Kruskal's algorithm)

**Time Complexity**: O(α(n)) per operation (nearly constant) where α is inverse Ackermann function
**Space Complexity**: O(n)

---

### 6. Two Pointers

**Definition**: Two pointers technique uses two pointers (indices) that traverse a data structure (usually an array or linked list) to solve problems efficiently, often reducing time complexity from O(n²) to O(n).

**Key Characteristics**:
- Two indices moving through the data structure
- Often one moves forward, one backward, or both move in same direction
- Works well with sorted arrays
- Can be used for: finding pairs, removing duplicates, palindrome checking, linked list problems

**When to Use**:
- Sorted array problems
- Linked list problems (finding middle, cycle detection, merging)
- Problems asking for pairs that sum to target
- Problems requiring O(1) space complexity
- Sliding window problems (variant of two pointers)

**Time Complexity**: Usually O(n)
**Space Complexity**: Usually O(1)

---

### 7. Binary Search

**Definition**: Binary search is a search algorithm that finds the position of a target value within a sorted array by repeatedly dividing the search interval in half.

**Key Characteristics**:
- Requires sorted data
- Divides search space in half each iteration
- Very efficient for large datasets
- Can be used for: searching in sorted arrays, finding boundaries, optimization problems

**When to Use**:
- Sorted array problems
- Finding insertion position
- Finding boundaries (first/last occurrence)
- Optimization problems (find minimum/maximum value satisfying condition)
- Problems with monotonic property

**Time Complexity**: O(log n)
**Space Complexity**: O(1) for iterative, O(log n) for recursive

---

### 8. Dynamic Programming (DP)

**Definition**: Dynamic Programming is a method for solving complex problems by breaking them down into simpler subproblems. It stores the results of subproblems to avoid recomputing them (memoization).

**Key Characteristics**:
- Overlapping subproblems
- Optimal substructure (optimal solution contains optimal solutions to subproblems)
- Can be top-down (memoization) or bottom-up (tabulation)
- Can be used for: optimization problems, counting problems, sequence problems

**When to Use**:
- Problems with overlapping subproblems
- Optimization problems (max, min, longest, shortest)
- Counting problems (number of ways)
- Sequence problems (strings, arrays)
- Problems that can be broken into smaller subproblems

**Time Complexity**: Usually O(n) or O(n²) depending on problem
**Space Complexity**: Usually O(n) or O(n²), can often be optimized to O(1)

---

### 9. Greedy Algorithm

**Definition**: A greedy algorithm makes the locally optimal choice at each stage with the hope of finding a global optimum. It doesn't reconsider previous choices.

**Key Characteristics**:
- Makes best choice at each step
- No backtracking
- Often faster than DP but may not always give optimal solution
- Can be used for: interval scheduling, minimum spanning tree, shortest path

**When to Use**:
- Problems with greedy choice property
- Problems where local optimum leads to global optimum
- Interval problems
- Problems where you can make a decision and never need to reconsider

**Time Complexity**: Usually O(n log n) due to sorting, or O(n)
**Space Complexity**: Usually O(1) or O(n)

---

### 10. Backtracking

**Definition**: Backtracking is a systematic method for exploring all possible solutions to a problem by building solutions incrementally and abandoning ("backtracking") partial solutions that cannot lead to a valid solution.

**Key Characteristics**:
- Explores all possibilities
- Abandons invalid paths early (pruning)
- Uses recursion with state restoration
- Can be used for: permutations, combinations, N-Queens, Sudoku

**When to Use**:
- Problems requiring all possible solutions
- Constraint satisfaction problems
- Problems with small constraints (n ≤ 20)
- Problems where you need to explore and backtrack

**Time Complexity**: Usually exponential, O(2^n) or O(n!)
**Space Complexity**: O(n) for recursion stack

---

### 11. Brute Force

**Definition**: Brute force is a straightforward approach that tries all possible solutions to find the correct one. It's often the first approach but may be inefficient.

**Key Characteristics**:
- Tries all possibilities
- Simple to implement
- May be inefficient for large inputs
- Can be used for: small constraint problems, when other approaches are unclear

**When to Use**:
- Small constraint problems (n ≤ 20)
- When no better approach is obvious
- As a starting point before optimization
- Problems where efficiency is not critical

**Time Complexity**: Usually exponential or polynomial
**Space Complexity**: Varies

---

### 12. Sliding Window

**Definition**: Sliding window is a technique for maintaining a subset of data (window) that slides through a larger dataset. It's efficient for problems involving contiguous subarrays/substrings.

**Key Characteristics**:
- Maintains a window of elements
- Expands or contracts the window based on conditions
- Efficient for contiguous subarray/substring problems
- Can be used for: maximum/minimum in subarray, substring problems, fixed/variable window size

**When to Use**:
- Contiguous subarray/substring problems
- Problems asking for maximum/minimum in a window
- Problems with "at most k" or "exactly k" constraints
- String problems with substring constraints

**Time Complexity**: Usually O(n)
**Space Complexity**: Usually O(1) or O(k) where k is window size

---

### 13. Prefix Sum

**Definition**: Prefix sum (or cumulative sum) is a technique that precomputes the sum of elements from the start of the array up to each index. This allows O(1) range sum queries.

**Key Characteristics**:
- Precomputes cumulative sums
- Enables O(1) range queries
- Useful for subarray sum problems
- Can be used for: range sum queries, subarray problems, difference arrays

**When to Use**:
- Subarray sum problems
- Range sum queries
- Problems asking for sum of elements in range [i, j]
- Problems that can be converted to sum problems

**Time Complexity**: O(n) preprocessing, O(1) per query
**Space Complexity**: O(n)

---

### 14. Heap / Priority Queue

**Definition**: A heap is a complete binary tree that satisfies the heap property (min-heap: parent ≤ children, max-heap: parent ≥ children). Priority queue is an abstract data type often implemented using heaps.

**Key Characteristics**:
- Efficiently maintains min/max element
- O(log n) insert and extract operations
- O(1) access to min/max
- Can be used for: finding kth largest/smallest, merging sorted lists, scheduling

**When to Use**:
- Finding kth largest/smallest element
- Problems requiring maintaining top k elements
- Merging multiple sorted sequences
- Problems with priority-based processing

**Time Complexity**: O(log n) for insert/extract, O(n log n) for heapify
**Space Complexity**: O(n)

---

### 15. Stack

**Definition**: A stack is a linear data structure that follows Last-In-First-Out (LIFO) principle. Elements are added and removed from the same end (top).

**Key Characteristics**:
- LIFO (Last In First Out)
- O(1) push and pop operations
- Useful for: parsing, expression evaluation, backtracking
- Can be used for: matching parentheses, next greater element, monotonic stack

**When to Use**:
- Parentheses matching problems
- Expression evaluation
- Next greater/smaller element problems
- Problems requiring LIFO order
- Monotonic stack problems (maintaining increasing/decreasing order)

**Time Complexity**: O(1) per operation, O(n) overall
**Space Complexity**: O(n)

---

## Flowchart Visualization

The flowchart is a decision tree that starts with a root question and branches based on your answers. Here's a text-based representation of the major paths:

```
START
│
├─ Is it a graph?
│  │
│  ├─ YES → Is it a tree?
│  │         │
│  │         ├─ YES → DFS
│  │         │
│  │         └─ NO → Is problem related to directed acyclic graph?
│  │                   │
│  │                   ├─ YES → Topological Sort
│  │                   │
│  │                   └─ NO → Is the problem related to shortest path?
│  │                             │
│  │                             ├─ YES → Is the graph weighted?
│  │                             │         │
│  │                             │         ├─ YES → Dijkstra's Algorithm
│  │                             │         │
│  │                             │         └─ NO → BFS
│  │                             │
│  │                             └─ NO → Does the problem involve connectivity?
│  │                                       │
│  │                                       ├─ YES → Disjoint Set Union
│  │                                       │
│  │                                       └─ NO → Does the problem have small constraints?
│  │                                                 │
│  │                                                 ├─ YES → Is brute force fast enough?
│  │                                                 │         │
│  │                                                 │         ├─ YES → Brute Force / Backtracking
│  │                                                 │         │
│  │                                                 │         └─ NO → Dynamic Programming
│  │                                                 │
│  │                                                 └─ NO → Need to solve for kth smallest/largest?
│  │                                                           │
│  │                                                           ├─ YES → Heap / Sorting
│  │                                                           │
│  │                                                           └─ NO → [Continue to other branches]
│  │
│  └─ NO → [Continue to array/string problems]
│
├─ About subarray or substring?
│  │
│  ├─ YES → Deal with sum or additive?
│  │         │
│  │         ├─ YES → Prefix Sum
│  │         │
│  │         └─ NO → Sliding Window
│  │
│  └─ NO → [Continue to other branches]
│
├─ Calculating max/min of something?
│  │
│  ├─ YES → Monotonic condition?
│  │         │
│  │         ├─ YES → Can be split into sub-problem?
│  │         │         │
│  │         │         ├─ YES → Greedily calculate answer?
│  │         │         │         │
│  │         │         │         ├─ YES → Greedy Algorithm
│  │         │         │         │
│  │         │         │         └─ NO → Dynamic Programming
│  │         │         │
│  │         │         └─ NO → Binary Search
│  │         │
│  │         └─ NO → [Continue to other branches]
│  │
│  └─ NO → [Continue to other branches]
│
├─ Asking for number of ways?
│  │
│  ├─ YES → Is brute force fast enough?
│  │         │
│  │         ├─ YES → Brute Force / Backtracking
│  │         │
│  │         └─ NO → Dynamic Programming
│  │
│  └─ NO → [Continue to other branches]
│
├─ Multiple sequence?
│  │
│  ├─ YES → Monotonic condition?
│  │         │
│  │         ├─ YES → Can split into sub-problem?
│  │         │         │
│  │         │         ├─ YES → Dynamic Programming
│  │         │         │
│  │         │         └─ NO → Two pointer
│  │         │
│  │         └─ NO → [Continue to other branches]
│  │
│  └─ NO → [Continue to other branches]
│
├─ Find or enumerate indices?
│  │
│  ├─ YES → Monotonic Condition?
│  │         │
│  │         ├─ YES → Two pointer
│  │         │
│  │         └─ NO → [Continue to other branches]
│  │
│  └─ NO → [Continue to other branches]
│
├─ O(1) memory required?
│  │
│  ├─ YES → Involve monotonic condition?
│  │         │
│  │         ├─ YES → Two pointer
│  │         │
│  │         └─ NO → Do you need to parse symbols?
│  │                   │
│  │                   ├─ YES → Stack
│  │                   │
│  │                   └─ NO → [Continue to other branches]
│  │
│  └─ NO → [Continue to other branches]
│
└─ Involve Linked List?
   │
   ├─ YES → Two pointer
   │
   └─ NO → [Continue to other branches]
```

---

## Decision Tree Structure

### Main Decision Points

The flowchart organizes decisions into several major categories:

#### 1. Graph Problems Branch
- **Is it a graph?** → If yes, proceed to graph-specific algorithms
  - **Is it a tree?** → If yes, use DFS
  - **Is problem related to directed acyclic graph?** → If yes, use Topological Sort
  - **Is the problem related to shortest path?** → If yes, check if weighted
    - **Is the graph weighted?** → If yes, use Dijkstra's Algorithm; if no, use BFS
  - **Does the problem involve connectivity?** → If yes, use Disjoint Set Union
  - **Does the problem have small constraints?** → If yes, check if brute force is fast enough
    - **Is brute force fast enough?** → If yes, use Brute Force/Backtracking; if no, use Dynamic Programming
  - **Need to solve for kth smallest/largest?** → If yes, use Heap/Sorting

#### 2. Array/String Problems Branch
- **About subarray or substring?** → If yes, check if dealing with sum
  - **Deal with sum or additive?** → If yes, use Prefix Sum; if no, use Sliding Window
- **Calculating max/min of something?** → If yes, check for monotonic condition
  - **Monotonic condition?** → If yes, check if can split into sub-problems
    - **Can be split into sub-problem?** → If yes, check if can greedily calculate
      - **Greedily calculate answer?** → If yes, use Greedy Algorithm; if no, use Dynamic Programming
    - If no, use Binary Search
- **Asking for number of ways?** → If yes, check if brute force is fast enough
  - **Is brute force fast enough?** → If yes, use Brute Force/Backtracking; if no, use Dynamic Programming
- **Multiple sequence?** → If yes, check for monotonic condition
  - **Monotonic condition?** → If yes, check if can split into sub-problems
    - **Can split into sub-problem?** → If yes, use Dynamic Programming; if no, use Two pointer
- **Find or enumerate indices?** → If yes, check for monotonic condition
  - **Monotonic Condition?** → If yes, use Two pointer
- **O(1) memory required?** → If yes, check for monotonic condition
  - **Involve monotonic condition?** → If yes, use Two pointer; if no, check if need to parse symbols
    - **Do you need to parse symbols?** → If yes, use Stack
- **Involve Linked List?** → If yes, use Two pointer

### Key Decision Criteria

Understanding these criteria will help you navigate the flowchart:

1. **Graph vs. Non-Graph**: Does the problem involve nodes and edges?
2. **Tree vs. General Graph**: Is it a connected acyclic graph?
3. **Weighted vs. Unweighted**: Do edges have weights/costs?
4. **Directed vs. Undirected**: Do edges have direction?
5. **Monotonic Condition**: Does the problem have a property that increases or decreases monotonically?
6. **Subproblems**: Can the problem be broken into smaller similar problems?
7. **Constraints**: How large is the input? (affects brute force feasibility)
8. **Memory Requirements**: Is O(1) space required?

---

## Runtime to Algorithm Mapping

When you know the required time complexity, you can work backwards to identify potential algorithms. This is useful when constraints are tight or when optimizing a solution.

### O(1) - Constant Time
- **Hash Map/Set operations**: Lookup, insert, delete (average case)
- **Array indexing**: Access by index
- **Stack/Queue operations**: Push, pop, peek (when implemented with arrays)

### O(log n) - Logarithmic Time
- **Binary Search**: Searching in sorted arrays
- **Heap operations**: Insert, extract min/max
- **Binary Search Tree**: Search, insert, delete (balanced trees)
- **Divide and Conquer**: Problems that halve the search space each step

### O(n) - Linear Time
- **Single pass through array**: One iteration through data
- **Two Pointers**: Both pointers traverse the array once
- **Sliding Window**: Window moves through array once
- **Tree traversal**: DFS/BFS visiting each node once
- **Hash Map iteration**: Iterating through all key-value pairs

### O(n log n) - Linearithmic Time
- **Sorting algorithms**: Merge sort, heap sort, quick sort (average)
- **Heap operations**: Building a heap from array
- **Divide and Conquer**: Problems that split and combine (like merge sort)
- **Greedy with sorting**: Many greedy algorithms require sorting first

### O(n²) - Quadratic Time
- **Nested loops**: Two nested iterations
- **Brute force**: Checking all pairs
- **Dynamic Programming**: Some 2D DP problems
- **Matrix operations**: Traversing 2D arrays

### O(2^n) - Exponential Time
- **Backtracking**: Generating all subsets, permutations
- **Recursive brute force**: Problems with exponential solution space
- **Brute force enumeration**: Trying all possibilities

### O(n!) - Factorial Time
- **Permutations**: Generating all permutations
- **Brute force**: Problems requiring trying all orderings

### Graph-Specific Complexities

#### O(V + E) - Vertices + Edges
- **DFS**: Depth-first search
- **BFS**: Breadth-first search
- **Topological Sort**: Kahn's algorithm or DFS-based

#### O((V + E) log V) - With Priority Queue
- **Dijkstra's Algorithm**: Shortest path with binary heap
- **Prim's Algorithm**: Minimum spanning tree

#### O(V²) or O(E log V)
- **Dijkstra's Algorithm**: Depending on implementation
- **Floyd-Warshall**: All pairs shortest path (O(V³))

### Space Complexity Considerations

#### O(1) - Constant Space
- **Two Pointers**: Only using a few variables
- **In-place algorithms**: Modifying input array
- **Iterative solutions**: No recursion stack

#### O(n) - Linear Space
- **Hash Map/Set**: Storing n elements
- **Recursion stack**: DFS with depth n
- **DP arrays**: 1D dynamic programming
- **Queue**: BFS storing at most width of tree

#### O(n²) - Quadratic Space
- **2D DP arrays**: Tabulation with 2D table
- **Adjacency matrix**: Dense graph representation

### Quick Reference: Problem Constraints → Algorithm

| Constraint Size | Typical Algorithms |
|----------------|-------------------|
| n ≤ 20 | Backtracking, Brute Force, Bitmask DP |
| n ≤ 100 | O(n³) algorithms, 3 nested loops |
| n ≤ 1,000 | O(n²) algorithms, 2 nested loops, 2D DP |
| n ≤ 10,000 | O(n log n) algorithms, sorting, binary search |
| n ≤ 100,000 | O(n) or O(n log n) algorithms |
| n ≤ 1,000,000 | O(n) algorithms, single pass, two pointers |

### Runtime Analysis Workflow

1. **Identify constraints**: What are the input sizes?
2. **Calculate required complexity**: What's the maximum acceptable time?
3. **Match to algorithm**: Which algorithms fit this complexity?
4. **Consider space**: Is there a space constraint?
5. **Verify**: Does the algorithm actually achieve this complexity?

---

## Additional Resources

### AlgoMonster Resources

1. **Runtime to Algorithm Cheat Sheet**
   - Link: [Runtime to Algo Cheat Sheet](https://algo.monster/runtime)
   - Description: Quick reference for matching time complexity requirements to algorithms

2. **Pattern-Based Learning**
   - Link: [Pattern-Based Learning](https://algo.monster/patterns)
   - Description: Overview of how patterns can help you learn and prepare for interviews faster

3. **Binary Search Introduction**
   - Link: [Binary Search Intro](https://algo.monster/binary-search)
   - Description: Deep dive into binary search pattern and applications

4. **Algorithm Templates**
   - Link: [Templates](https://algo.monster/templates)
   - Description: Ready-to-use code templates for common algorithms

5. **Flowchart (Interactive)**
   - Link: [Flowchart](https://algo.monster/flowchart)
   - Description: Interactive version of the decision tree

### Other Useful Tools

1. **{ Runtime: Algo } Tool**
   - Description: Find algorithms based on complexity requirements
   - Use Case: When you know the required time/space complexity, find matching algorithms
   - Example: Input "O(n log n)" → Returns algorithms like sorting, heap operations, divide and conquer

2. **{ Keyword: Algo } Tool**
   - Description: Search for algorithms using specific keywords from problem statements
   - Use Case: Extract keywords from problem description to find relevant algorithms
   - Example: Keywords like "sorted array", "shortest path", "maximum" → Suggests binary search, Dijkstra, DP

3. **Algorithm Templates**
   - Link: [Templates](https://algo.monster/templates)
   - Description: Ready-to-use code templates for common algorithms
   - Includes: DFS, BFS, Binary Search, Two Pointers, DP, Backtracking, and more
   - Benefits: Saves time, ensures correct implementation, provides starting point

4. **Practice Lists**
   - **Monster 50**: Essential 50 problems covering core patterns
   - **Blind 75**: Popular list of 75 must-solve problems
   - **Monster DP List**: Comprehensive dynamic programming problems
   - **Speedrun**: Quick multiple-choice problems for pattern recognition training

5. **Company-Specific Problems**
   - Description: Interview guides and questions categorized by specific companies
   - Use Case: Targeted preparation for specific company interviews
   - Includes: Google, Facebook, Amazon, Microsoft, Apple, and more

6. **Core Patterns Course**
   - Description: Comprehensive learning experience focused on pattern-based problem-solving
   - Covers: All major algorithmic patterns with detailed explanations
   - Includes: Practice problems, solutions, and pattern recognition exercises

7. **Foundation Course**
   - Description: Beginner-friendly course covering basic data structures and algorithms
   - Ideal for: Those new to coding interviews
   - Covers: Arrays, linked lists, trees, graphs, sorting, searching basics

8. **System Design Resources**
   - Description: Resources dedicated to designing scalable systems
   - Important for: Higher-level technical interviews (L4+ at most companies)
   - Covers: Scalability, distributed systems, database design, caching strategies

9. **Build an LLM from Scratch**
   - Description: Course teaching how to build a Large Language Model
   - Prerequisites: No prior machine learning experience required
   - Focus: Understanding LLM architecture and implementation

---

## How to Practice with This Guide

### Step 1: Understand the Algorithms
Before using the flowchart, make sure you understand what each algorithm does. Review the [Algorithm Definitions](#algorithm-definitions-endpoints) section.

### Step 2: Start with the Flowchart
When you encounter a new problem:
1. Read the problem carefully
2. Start at the root of the flowchart
3. Answer each question based on the problem description
4. Follow the path until you reach an algorithm endpoint

### Step 3: Verify Your Choice
After identifying the algorithm:
1. Think about why this algorithm fits
2. Consider the time/space complexity
3. Check if there are alternative approaches

### Step 4: Implement and Refine
1. Implement the solution using the identified algorithm
2. Test with edge cases
3. Optimize if necessary

### Step 5: Reflect and Learn
1. After solving, reflect on the decision path you took
2. Note any patterns you recognized
3. Consider if you could have identified the algorithm faster

---

## Common Patterns and Their Indicators

### Graph Indicators
- Keywords: "network", "connections", "relationships", "nodes", "edges"
- Problems involving: social networks, maps, dependencies

### Tree Indicators
- Keywords: "hierarchy", "parent-child", "root", "leaf"
- Problems involving: file systems, organizational structures, binary trees

### Dynamic Programming Indicators
- Keywords: "maximum", "minimum", "longest", "shortest", "number of ways"
- Overlapping subproblems
- Optimal substructure
- Often involves sequences (arrays, strings)

### Two Pointers Indicators
- Sorted arrays
- Linked lists
- Finding pairs
- O(1) space requirement

### Binary Search Indicators
- Sorted data
- Finding boundaries
- Optimization problems (min/max satisfying condition)
- Monotonic property

### Greedy Indicators
- Local optimum leads to global optimum
- Interval problems
- Problems where you make a decision and never reconsider

### Backtracking Indicators
- Generate all possibilities
- Constraint satisfaction
- Small constraints (n ≤ 20)
- Problems requiring exploration with pruning

---

## Tips for Effective Problem Solving

1. **Don't Rush**: Take time to understand the problem before jumping to solutions
2. **Use the Flowchart**: Even if you think you know the answer, go through the flowchart to reinforce the decision process
3. **Practice Pattern Recognition**: The more problems you solve, the faster you'll recognize patterns
4. **Understand, Don't Memorize**: Focus on understanding why an algorithm fits, not just memorizing when to use it
5. **Start Simple**: Begin with brute force if needed, then optimize
6. **Consider Edge Cases**: Always think about empty inputs, single elements, duplicates, etc.
7. **Analyze Complexity**: Always consider time and space complexity
8. **Review Solutions**: After solving, review optimal solutions to learn new techniques

---

## Conclusion

The AlgoMonster flowchart is a powerful tool for systematic problem-solving. By understanding the algorithms and following the decision tree, you can approach any LeetCode problem with confidence. Remember:

- **Pattern recognition comes with practice**
- **The flowchart is a guide, not a rule**
- **Understanding > Memorization**
- **Start simple, optimize later**

Happy coding! 🚀

---

*Last Updated: Based on AlgoMonster flowchart as of 2024*
*Source: [AlgoMonster Flowchart](https://algo.monster/flowchart)*

