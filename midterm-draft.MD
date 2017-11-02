# OVERVIEW 

## :star: Key :star:
**:star: = section header (\##)**  
**:small_blue_diamond: = subsection header (\###)**  
**:heavy_plus_sign: = section header (\##) for topic not in study guide/review lecture but possibly worth knowing for exam(??)**

## :star: Topics :star:
- [Definitions](#definitions)
- [Stacks and Queues](#stacks-and-queues)
- [Runtime Analysis](#runtime-analysis)
- [Dictionaries](#dictionaries)
- [BSTs](#bsts)
- [Traversals](#traversals)
- [AVL Trees](#avl-trees)
- [Hash Tables](#hash-tables)
- [Memory Hierarchy](#memory-hierarchy)
- [B+-trees](#b+-trees)
- [Priority Queues](##priority-queues-adt)
- [Heaps](#heaps)

## :star: Exam Breakdown :star:
### :small_blue_diamond: General Info :small_blue_diamond:
- 6-8 questions
- Focus on topic covered in review, though anything covered is fair game
- Time management is key
- No writing code. Might have pseudocode like question 5 on the homework, where you’re give a problem and asked to walk through the solution (how how your algorithm finds the solution and be able to provide runtime analysis for it). 
- Also might be given code to debug or calculate the runtime for it. 

### :small_blue_diamond: Question-Specific :small_blue_diamond:
- ALSO SEE THE TOPICS BELOW FOR MORE INFO  
- Q1 is short answer but will have many parts. 
  - It may be best to save this for last because each is time-consuming for a number of points they're worth individually.
  - Multiple questions in this, all with varying difficulty.
  - Might include an equation of a recurrence.
- Q2 is algorithm analysis
  - Just like problem 2 on the homework, meaning you will be given some code and need to provide bigO bound
  - Expect for loops and recursion
  - Show work for partial credit
- AVL
  - Given an input sequence, have to insert into the AVL tree, and show each time there is a rotation
  - Show work for partial credit
  - Check to make sure final tree is actually an AVL tree (i.e. balanced and a BST)
  - Not expected to do deletion, but lazy deletion might show up on the short answer. (Same goes for B+-Trees)
- Hash tables
  - Insert using linear probing, quadratic probing, secondary hashing, and chaining
- Priority Queues/Heaps
  - Percolate up, percolate down and represent in both tree and array form
  - Draw a tree with a bunch of insertions and then at the end produce the array form. 

**[Back to top :rocket:](#overview)**

--------------------------

# DEFINITIONS

## :star: Abstract Data Type (ADT) :star:
- **Has expected behavior**
- **Can't be analyzed asymptotically by itself, as need to know how the data is structured**  
- **Examples**
  - Stacks  
  - Queues  
  - Priority Queues  
  - Dictionary (i.e. map) 
    - Supports functions: insert, find, delete

## :star: Data Structure :star:
- **Language independent structure which implements an ADT**  
- **Can be analyzed asymptotically**  
- **Examples**
  - Arrays 
  - LinkedList
  - Binary Search Trees (BST)
  - AVL Trees  
  - Hashtables  
  - B Trees (i.e. B+ Trees)  
  - Heaps

## :star: Implementation :star:
- **Low-level design decisions**
  - Example: when using a heap, do we use 0 indexing or 1 indexing? :question:
- **Language specific**
  - It doesn't change asymptotic performance, but it is language specific design decisions that we can make. 

## :star: Summary/Other Relevant Info :star:
- **Know the different levels**
  - Implementation is the lowest level (actual code considers this)
  - Data structure is higher than implementation
  - ADT is totally separate from the data and is just behavior and functions
- **Examples**
  - The Queue ADT supports enqueue, dequeue and front, and the ADT includes FIFO.
  - Arrays and Linked Lists are examples of the data structures.
  - Implementation: how we include front and back pointers to make implementation easier.
- **Summary of ADT vs. Data Structures**
  - The ADT describes the methods provided and the behavior we expect from them.
  - The Data Structure is a theoretical arrangement of the data that supports the functionality of the ADT
  
## :heavy_plus_sign: Testingn :heavy_plus_sign: 
- **Two primary types of testing**  
  - Black box
    - Behavior only, no peeking into the code
    - This usually tests ADT behavior
    - Can test performance/efficiency by using a timer
  - White box (or clear box)
    - Where there is an understanding of the implementation that can be leveraged for testing
    - If you’re writing your own DS, you can peek into attributes that you would normally refuse access to the client  
- **Good things to test**
  - Expected behavior (at multiple sizes)
  - Forbidden input
  - Empty/Null
  - Side effects
  - Boundary/Edge Cases

**[Back to top](#overview)**

--------------------------

# STACKS AND QUEUES

## :star: Stack :star:
- **Supports: push(), pop(), top()**
  - Push(Object a) returns null; (other options?)
  - Pop() returns Object a: where a is the element on ‘top’ of the stack; also removes a from the stack
  - Top() returns Object a: where a is the element on ‘top’ of the stack without removing that element from the
- **LIFO order**
  - Last In, First Out

## :star: Queue :star:
- **Supports: enqueue(), dequeue(), front()**
  - enqueue(Object toInsert): adds to the queue
  - dequeue(): removes the ‘next’ element from the queue
  - front(): peeks at the ‘next’ element
- **FIFO order**
  - First In, First Out

## :heavy_plus_sign: Why behavior is important :heavy_plus_sign:
- **Stacks and Queues both support the same functions**
  - insert: push() and enqueue()
  - remove: pop() and dequeue()
  - peek: top() and front()
- **This isn’t sufficient to distinguish them, their behavior is also a critical part of their ADT. FIFO v LIFO**

## :star: Data structure choices :star:
- Arrays and Linked Lists
- Considerations
  - Memory usage
  - Ease of implementation
  - Resizing time (comes up for arrays)
  - Memory hierarchy (often gives an advantage to arrays) 
- Runtimes:
  - O(1) for all functions (when front and back pointers are implemented correctly), except when resizing.
  - They constrain our access to the data so severely that were able to get really quick run times from them. 

**[Back to top](#overview)**

--------------------------

# RUNTIME ANALYSIS

## :star: Basics :star:
- **Counting the number of operations**  
  - Comparisons, mathematical operations, assignments 
- **For loops and while statements**  
  - Count the number of times relevant code is executed
  - Multiply opperations
- **Important summations**
  - Sum of all numbers (powers??) from 1 to n
  
  - Sum of the powers of two
  - Sum of all the inverse of two

## :star: Asymptotic Analysis :star:
- **Best-case, worst-case, average-case**  
- **Usually we discuss worst-case complexity**  
- **If we increase the input size, how does the computation time change**  

## :star: BigO notation :star:
- **Upper bound for a given function**  
- **f(n) = O(g(n) if there exists a c and n0 for which f(n) < c\*g(n) for all n > n0**  

## :star: Recurrences :star:
### :small_blue_diamond: Steps :small_blue_diamond:
- Analysis of recursive functions
- Break the function into recursive and non-recursive
- Produce the recurrence relation
- Roll out the recurrence or produce the recurrence tree
- Find the closed form of the recurrence
- Upper bound this recurrence with a bigO bound.

### :small_blue_diamond: Example :small_blue_diamond:

``` java
reverse(Node L):
  if(L == null) return L;               non-recursive O(1)
  else if(L.next == null) return L;     non-recursive O(1)
  else
    Node front = L                      non-recursive O(1)
    Node rest = L.next                  non-recursive O(1)
    L.next = null                       non-recursive O(1)
    Node restRev = reverse(rest)        recursive
    appendToEnd(front,restRev)          non-recursive O(n)
```

What is the total runtime then? T(n) = c₀ + c₁\*n + **recursive work**  
What is the recursive work? rest is size n-1  
So...T(n) = c₀ + c₁\*n + **T(n-1)**


**Recurrence relation for reverse**  
T(n) = d₀ when n = 0  
T(n) = d₁ when n = 1  
T(n) = c₀ + c₁\*n + T(n-1) when n > 1

**How do we solve this recurrence? We can unroll it and see if a pattern emerges**  
```
T(n) = c₀ + c₁*n + T(n-1) 
                   __↓___________________
T(n) = c₀ + c₁*n + c₀ + c₁*(n-1) + T(n-2)  
                                   __↓___________________
T(n) = c₀ + c₁*n + c₀ + c₁*(n-1) + c₀ + c₁(n-2) + T(n-3)  
       __       _______________   _____
T(n) = 3c₀ + c₁*(n+(n-1)+(n-2)) + T(n-3)
```

**What are the patterns?**
- Each time we add 1 c₀
- Each time we add ‘n’ c₁
- But n is getting reduced by one every time
- How many times does this call itself?
  - n-1, because 1 is a base case
- What then is the closed form of this recurrence?
   - T(n) = (n-1) * c₀ + Σi * c₀
   - T(n) = (n-1) * c₀ + (n-1) * (n)/2 * c₁
   - T(n) = (n-1) * c₀ + (n-1) * (n)/2 * c₁ + d₁
   - What is the upper bound of this function?
    - O(n²) the O(n) appendToEnd is what costs us
- While this process is important, we can save some steps if all we care about is the upper bound
  - bigO notation eliminates the need for constants
  - Lots of our messing around with c0 and c1 doesn’t come through to the solution
  - Rather than saying T(n) = c₀ + n * c₁ + T(n-1), we can observe that c₀ + n * c₁ is in O(n)
  - Simplify to T(n) = O(n) + T(n-1)

## :star: Amortized analysis :star:
- **Used when an expensive operation occurs with predictable frequency (e.g. resizing an array)**  
- **Describe the state of the data structure**  
- **Indicate the number of operations**  
- **Determine how many are the costly operation and how many are the cheap operations**  
- **# of costly * costly runtime + # cheap * cheap runtime**  
- **Divide by the number of operations**  

## :star: Memory analysis :star:
- **Calculating how much memory an algorithm needs**  
- **This is in addition to the data itself**  
- **Think about any secondary data structures you might use**  
- **Also, remember that recursive functions consume memory on the call stack**  

## :star: Basic Idea :star:
- If we increase the size of the input by one, how does our total computation change?
- O(1): Input size has no effect on runtime
- O(log n): doubling the input increases the runtime by some constant amount
- O(n): linear time, each additional input increases execution time by a constant amount
- O(n²): doubling the input increases the runtime by a factor of 4.
- O(2ⁿ): exponential, increasing the input by one doubles the runtime

**[Back to top](#overview)**

--------------------------

# DICTIONARIES

## :star: Functions :star:
- **Insert(key k, value v)**
- **find(key k)**
- **delete(key k)**

## :star: Additional Properties :star:
- Data is stored in key, value pairs
- In this course, duplicate keys are not allowed
- Most data structures can implement a dictionary

**[Back to top](#overview)**

--------------------------

# BSTs

## :star: Properties :star:
- Binary trees
- Nodes with two children
- Maintains search property
  - All values in the left subtree must be less than the parent
  - All values in the right subtree must be greater than the parent
- With each increase in height, the number of nodes in a tree roughly doubles
- A perfect tree has 2<sup>h+1</sup> -1 nodes 
- Roughly half of a binary search tree are leaves

**[Back to top](#overview)**

--------------------------

# TRAVERSALS

## :star: Two main traversal families :star:

### :small_blue_diamond: Depth First Search (DFS) :small_blue_diamond:
- Usually implemented recursively
- Whether the parent is processed before, after or in the middle of its children determines if the traversal is pre-order, post-order or in-order respectively

### :small_blue_diamond: Breadth First Search (BFS) :small_blue_diamond:
- Put the root into a queue
- Dequeue a node, process it and enqueue its children
- Top to bottom left to right traversal
- Queue is largest at the widest part of the tree

**[Back to top](#overview)**

--------------------------

# AVL TREES

## :star: Properties :star:
- Specific type of binary search tree
- Still must implement binary search
- Nodes in AVL trees have two extra fields, height and balance
- Balance = | height(left) – height(right) |
- Balance for each node must be less than or equal to 1
- Trees with this condition still have O(log n) height
- No covering delete in this course
- Find: O(log n)
- Insert O(log n)

## :star: AVL Rotations :star:
- AVL Rotations occur when an insertion makes a node out of balance
- Relative to the node that is unbalanced, there are four rotations depending on which grandchild received the new node.
- Left-left and right-right rotations involve the child of the affected node being rotated up into position
- Left-right and right-left rotations involve the grandchild being rotated up into position. The grandparent and parent become the two children
- It is important that these rotations preserve BST property

**[Back to top](#overview)**

--------------------------

# HASH TABLES

## :star: Properties :star:
- A large data set M with a smaller set that should be saved, D
- A hash function maps M onto D
  - It should run in O(1) time
  - It should distribute into all of the available spots evenly
- Hashtables provide O(1) runtime IF
  - Collisions are not a problem
  - Decrease the chance of collisions by increasing the amount of memory (load factor)
    - Resizing is costly
- 2 ways to handle collisions
  1. Probing
    - Linear
    - Quadratic
    - Secondary Hashing
  2. Chaining

## :star: Probing :star:

### :small_blue_diamond: Linear probing :small_blue_diamond: 
- Try the appropriate hash table row first
- Increase the index by one until a spot is found
- Guaranteed to find a spot if it is available
- If the array is too full, its operations reach O(n) time. Primary clustering

### :small_blue_diamond: Quadratic Probing :small_blue_diamond: 
- Rather than increasing by one each time, we increase by the squares
- k+1, k+4, k+9, k+16, k+25
- Certain tables can cause secondary clustering
- Can fail to insert if the table is over half full

### :small_blue_diamond: Secondary Hashing :small_blue_diamond: 
- If two keys collide in the hash table, then a secondary hash indicates the probing size
- Need to be careful, possible for infinite loops with a very empty array
- If the secondary hash value and the table size are coprime (they share no factors), then secondary hashing will succeed if there is an open space
- If table size is prime, only need to check if hash is a multiple

### :star: Chaining :star:
- Rather than probing for an open position, we could just save multiple objects in the same position
- Some data structure is necessary here
- Commonly: a linked list, AVL tree or secondary hash table.
- Resizing isn’t necessary, but if you don’t, you will get O(n) runtime.

**[Back to top](#overview)**

--------------------------

# MEMORY HIERARCHY

## :star: Memory is not uniformly accessible :star:
- OS manages access to computer resources
- Some memory is on disk and some is in cache
- Dictated by two types of behavior
  - Spatial locality – Items near each other are moved together (memory pages)
  - Temporal locality – memory used recently will be used again

**[Back to top](#overview)**

--------------------------

# B+-TREES

## :star: Properties :star:
- To reduce disk accesses we introduce the B-tree
- Two types of nodes
  - Signposts: Have M pointers and M-1 keys
  - Leaves: Have L <K,V> Pairs and a pointer to the next leaf
- Signposts must have at least M/2 pointers and leaves must have at least L/2 data points, unless it is the root
- Keys in signposts are the smallest item in the next pointer

## :star: Insert :star:
- Find the leaf that should hold the inserted element
- Insert the new k,v pair in sorted order in the leaf node
- If it overflows (i.e. the leaf is full when inserted)
  - Split the leaf into two nodes and add the new leaf to the parent
- If the signpost overflows, split the signpost into two signposts and try to add the new signpost to the parent
- Split back up to the root and create a new root if necessary

**[Back to top](#overview)**

--------------------------

# HEAPS

## :star: Priority Queues ADT :star:
- Supports: insert(), findMin(), deleteMin(), changePriority()
- Data is stored in priority, value pairs
- In this class, we use the min-heap, where a lower value means it should dequeue first

## :star: Data Structure :star:

### :small_blue_diamond: Heap:small_blue_diamond:
- Complete binary tree
- Heap property

### :small_blue_diamond: Implementation :small_blue_diamond:
- Array
- Find parents/children arithmetically

### :small_blue_diamond: Runtimes :small_blue_diamond: 
- Insert: O(log n), findMin: O(1), deleteMin O(log n)
- ChangePriority: O(log n)
- buildHeap, O(n)

## :star: Percolate :star:

### :small_blue_diamond: Percolate up :small_blue_diamond: 
- After you’ve inserted an element in the next location in order to preserve completeness
- Compare the current element against its parent
- Swap if the child is less than the parent
- Repeat until the child is greater than the parent or the new element is swapped up to the root

### :small_blue_diamond: Percolate down :small_blue_diamond: 
- After deleting an element, move the last element (from completeness) up to the root
- Compare the current node against both of its children
- Swap the node with the smaller child provided the child is still smaller than the parent
- Continue until the node is smaller than both children, or it is a leaf.

## :star: Floyd’s method :star:
- For each element in the array from size/2 to the first element
- Percolate that element down as much as necessary
- Because most elements are near the bottom, they do not need to percolate down very far, this results in O(n) overall runtime

**[Back to top](#overview)**

--------------------------
