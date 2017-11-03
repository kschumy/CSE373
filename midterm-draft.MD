# OVERVIEW 

## :star: Key :star:
**:star: = section header (\##)**  
**:small_blue_diamond: = subsection header (\###)**  
**:triangular_flag_on_post: = something that was strongly emphasized as important or tricky**  
**:question: = something I'm very confused about/don't know and need to learn**  
**:heavy_plus_sign: = section header (\##) for topic not in study guide/review lecture but might be worth knowing for exam(??)**

--------------------------

## :star: Topics :star:
[Definitions](#definitions)  
[Stacks and Queues](#stacks-and-queues)  
[Runtime Analysis](#runtime-analysis)  
[Dictionaries](#dictionaries)  
[BSTs](#bsts)  
[Traversals](#traversals)  
[AVL Trees](#avl-trees)  
[Hash Tables](#hash-tables)  
[Memory Hierarchy](#memory-hierarchy)  
[B+-trees](#b+-trees)  
[Priority Queues](##priority-queues-adt)  
[Heaps](#heaps)

--------------------------

## :star: Exam Breakdown :star:
### :small_blue_diamond: General Info :small_blue_diamond:
- 6-8 questions
- Focus on topic covered in review, though anything covered is fair game
- Time management is key
- No writing code. Might have pseudocode like question 5 on the homework, where you're given a problem and asked to walk through the solution (how your algorithm finds the solution and be able to provide runtime analysis for it). 
- Also, might be given code to debug or calculate the runtime for it. 

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
  - Check to make sure final tree is actually an AVL tree (i.e. balanced and a BST) :triangular_flag_on_post:
  - Not expected to do deletion, but lazy deletion might show up on the short answer. (Same goes for B+-Trees)
- Hash tables
  - Insert using linear probing, quadratic probing, secondary hashing, and chaining
- Priority Queues/Heaps
  - Percolate up, percolate down and represent in both tree and array form
  - Draw a tree with a bunch of insertions and then at the end produce the array form. 

<br>  

**[Back to top :rocket:](#overview)**  

--------------------------
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

--------------------------

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

--------------------------

## :star: Implementation :star:
- **Low-level design decisions**
  - Example: when using a heap, do we use 0 indexing or 1 indexing? [Answer](#small_blue_diamond-implementation-small_blue_diamond)
- **Language specific**
  - It doesn't change asymptotic performance, but it is language specific design decisions that we can make. 

--------------------------

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

--------------------------

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

**[Back to top :rocket:](#overview)**

--------------------------
--------------------------

# STACKS AND QUEUES

## :star: Stack :star:
- **Supports: push(), pop(), top()**
  - Push(Object a) returns null; (other options?)
  - Pop() returns Object a: where a is the element on ‘top’ of the stack; also removes a from the stack
  - Top() returns Object a: where a is the element on ‘top’ of the stack without removing that element from the
- **LIFO order**
  - Last In, First Out

--------------------------

## :star: Queue :star:
- **Supports: enqueue(), dequeue(), front()**
  - enqueue(Object toInsert): adds to the queue
  - dequeue(): removes the ‘next’ element from the queue
  - front(): peeks at the ‘next’ element
- **FIFO order**
  - First In, First Out

--------------------------

## :heavy_plus_sign: Why behavior is important :heavy_plus_sign:
- **Stacks and Queues both support the same functions**
  - insert: push() and enqueue()
  - remove: pop() and dequeue()
  - peek: top() and front()
- **This isn’t sufficient to distinguish them, their behavior is also a critical part of their ADT. FIFO v LIFO**

--------------------------

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

**[Back to top :rocket:](#overview)**

--------------------------
--------------------------

# RUNTIME ANALYSIS

## :star: Basics :star:
- **Counting the number of operations**  
  - Comparisons, mathematical operations, assignments 
  - Sum of time of each statement
- **For loops and while statements**  
  - Count the number of times relevant code is executed
  - Number of itera+ons ∗ Time for Loop Body  
- **Floor** :heavy_plus_sign:
  - ⎣X⎦ = Floor function: the largest integer < X  
  - Examples:
    - ⎣2.7⎦ = 2 
    - ⎣−2.7⎦ = −3 
    - ⎣2⎦ = 2
- **Ceiling** :heavy_plus_sign:
  - ⎡X⎤ = Ceiling function: the smallest integer > X  
  - Examples:
    - ⎡2.3⎤ = 3 
    - ⎡−2.3⎤ = −2
    - ⎡2⎤ = 2

--------------------------

## :star: Important Summations :star: 
Name | Formula |
---- | --------- |
**Sum of all numbers from 1 to n = n(n+1)/2** | ![alt text][sumof1ton] |
**Sum of the powers of two** | ![alt text][sumofpowersof2]<br>See [Lecture from 10/6](https://uw.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=ef17e934-0508-4b67-89c1-4f5cf8382a76) - start at about 40:00 |
**Sum of all the inverse of two = 1** | ![alt text][sumofinversepowersof2] |

--------------------------

## :star: Asymptotic Analysis :star:
- [Panopto of lecture on 10/9](https://uw.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=c3a3d656-d56b-45ce-9c49-8c30e0dc99e2)
- Once we get enough data structure, how does our behavior change?
- **Best-case, worst-case, average-case.** Usually, we discuss worst-case complexity  
- **If we increase the input size, how does the computation time change**  

--------------------------

## :star: BigO notation :star:
- **Upper bound for a given function  
- **f(n) = O(g(n)) if there exists a c and n₀ for which f(n) < c\*g(n) for all n > n₀** 
- Must **mathmatically prove** the c and n₀ are sufficent. How to do this: start with some algebraic fact and perform mutations on it in order to get something in this form. 

--------------------------

## :star: Recurrences :star:
**:question: this whole section :question:**

### :small_blue_diamond: Steps :small_blue_diamond: 
1. Analysis of recursive functions  
2. Break the function into recursive and non-recursive  
3. Produce the recurrence relation (i.e. T(n))  
4. Options (pick one)
    1. Roll out the recurrence
        - works better when there's only one child (so there's only one sub-operation)
    2. Produce the recurrence tree
        - almost always used when there's more than one child
        - [Lecture from 10/6](https://uw.hosted.panopto.com/Panopto/Pages/Viewer.aspx?id=ef17e934-0508-4b67-89c1-4f5cf8382a76) **start at about 40:00**
        - How to do this:
          - Calculate the work at each row and then sum all of the rows.
          - It's **not** always the case that it's just the work in each row times the height. A lot of the times the work in each row is different. This is where you're going to use a lot of those [summations](#star-important-summations-star) (sum of all numbers n, sum of the powers of 2, etc). 
          - Often can get log(n) height, but this does not mean that you get log(n) runtime. Example: T(n) = 1 + 2(T(n/2)) = O(n) <- see link above from lecture on 10/6
5. Find the closed form of the recurrence
6. Upper bound this recurrence with a bigO bound.

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

--------------------------

## :heavy_plus_sign: Master theorem :heavy_plus_sign:
- These recurrences all follow a similar pattern
- Therefore, if you can produce a recurrence, there is actually a procedural way to produce solutions
- If T(n) = a * T(n / b) + nᶜ for n > n₀ and **if the base case is a constant**  

--------------------------

## :star: Amortized analysis :star:
- **Used when an expensive operation occurs with predictable frequency (e.g. resizing an array)**  
- **Steps to describe doing an amortized analysis on the midterm:** 
  - Describe the state of the data structure at the beginning. (such as, “the array is full and has *n* elements”). 
  - Indicate the number of operations. (“Perform *n* insertions”). 
  - Determine how many costly operations there are and how many cheap operations there is there are.
    - The reason that this is important is because the answer depends on these two. If the array is full and has *n* elements and then we add *n* more (provided that we're doubling the size of the array), we can restrict the fact that there is exactly one costly operation, i.e. exactly one resize.
  - Calculate amortized analysis...
```
(# of costly operations * costly runtime) + (# of cheap operations * cheap runtime)     total runtime
―――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――――  =  ―――――――――――――――
                                # of operations                                         # of operations
```
- **Important to note**
  - Amortized analysis is different than best case or worst case. It is a separate type of analytical case.
  - So far we've only seen examples where the cheap runtime is constant, but be prepared for a non-constant cheap runtime on the midterm. Be able to apply the run times for that case. :triangular_flag_on_post:

--------------------------

## :star: Memory analysis :star: :question:
- **Calculating how much memory an algorithm needs**, not for a data structure. **This is in addition to the data itself.** So if we have our data stored in AVL tree and we want to see how much memory it takes to do a recursive find, we don't include the data structure itself. 
- **Think about any secondary data structures you might use.**  If you have a queue and you're doing a breadth first search traversal, the Q is a secondary data structure that the algorithm itself requires. You want to consider how that data structure might be used, when it will be most full, and what elements are going to be in there.
- **Also, remember that recursive functions consume memory on the call stack.**  When you have a recursive function, every time you call that recursive function you add another block on to the call stack. This consumes memory there, thus consuming extra memory. 

--------------------------

## :star: Basic Idea :star:
- If we increase the size of the input by one, how does our total computation change?
- Expect these and ideas related to them in the short answer section.
- Runtime families
  - O(1): Input size has no effect on runtime
  - **O(log n)**: doubling the input increases the runtime by some constant amount
  - O(n): linear time, each additional input increases execution time by a constant amount
  - **O(n²)**: doubling the input increases the runtime by a factor of 4.
    - Be able to describe in a meaningful way how the runtime changes, specifically that to double the input increases the runtime by a factor of 4.
  - O(2ⁿ): exponential, increasing the input by one doubles the runtime

**[Back to top :rocket:](#overview)**

--------------------------
--------------------------

# DICTIONARIES

## :star: Properties of Dictionaries :star:
- **Operations**
  - insert(key k, value v): inserts the key, value pair into the dictionary. Overwrites the old value if the key is already in the dictionary.
  - find(key k): returns the stored value for a particular key in the dictionary, returns null if not found.
  - delete(key k): removes the key, value pair denoted by the key from the dictionary.
- **Additional Properties**
  - Data is stored in key, value pairs
  - In this course, duplicate keys are not allowed
  - Most data structures can implement a dictionary.
  - Differs from sets, which have no values and only cares if a key is present or not. Though set also and ADT and has find, insert and delete.

**[Back to top :rocket:](#overview)**

--------------------------
--------------------------

# BSTs

## :star: BSTs Properties :star:
- Binary trees, where each node has at most two children
- Maintains search property
  - All values (which are keys) in the left subtree must be less than the parent
  - All values (which are keys) in the right subtree must be greater than the parent
- All, subtrees must also be binary search trees. With this property, all binary search trees have sorted in-order traversals. 
- When implementing with a dictionary...
  - Insert() and find() remain similar
  - Key is the primary comparison
  - Value is attached to the key
  - Dictionary fact: All values have an associated key
  - All keys are unique, i.e. each key only has one value
- https://algs4.cs.princeton.edu/32bst/

--------------------------

## :star: BSTs Height and Node Count :star:
- Height of an empty tree = -1. Height of a single node = 0. 
- Height = 1 + max(height(left),height(right)) 
- With each increase in height, the number of nodes in a tree roughly doubles. This is where we start to get *log n* behaviour
- Roughly half of a binary search tree are leaves
- For a BST of height h: :question: is this section correct?
  - max # of leaves: 2ʰ ← perfect tree
  - max # of nodes: 2ʰ⁺¹ - 1 ← perfect tree 
  - max # of internal nodes: 2ʰ - 1 ← perfect tree
  - min # of nodes: h + 1
  - min # of nodes in a full BST: 2h + 1
  - # of leaf nodes in a perfect BST: (n + 1) / 2
- For a BST with n nodes inserted in arbitrary order 
  - Average height is O(log N)
  - Worst case height is O(N)

--------------------------

## :star: BSTs Analysis :star:
- Find()
  - Worst-case: O(n) ← when the tree is linear
  - Best-case: O(1) ← when the item is the root
  - Generally, however: O(log n) when the tree is balanced 
- Insert()
  - Worst case: O(n)
  - Best case: O(1)
  - General case depends on height of the tree
- Delete():
  - Some cases
    - The element is not in the data structure: don’t change the data, possibly throw an exception
    - The key is a leaf in the tree: remove the pointer to that node
    - The node has one child: replace that node with its child
    - The node has two children: “delete” it by overwriting the node with a different <key, value> pair
      - In order to avoid changing the shape and doing too much work, it must be either the predecessor (the element just before it in sorted order) or the successor (the element just after it in sorted order).
  - Worst case(): O(n), finding the predecessor/successor takes time, esp. in very unbalanced tree.
  - Best case(): O(1) if we’re deleting the root from a degenerate tree (“Degenerate” trees are those that are very unbalanced) 
  - Generally, however: O(log n) when the tree is balanced 

**[Back to top :rocket:](#overview)**

--------------------------
--------------------------

# TRAVERSALS

:question: this whole section :question:

## :star: Two main traversal families :star:

### :small_blue_diamond: Depth First Search (DFS) :small_blue_diamond:
- Usually implemented recursively. So if you're doing memory analysis, the call stack is important.
- Whether the parent is processed before, after or in the middle of its children determines if the traversal is pre-order, post-order or in-order respectively. 

### :small_blue_diamond: Breadth First Search (BFS) :small_blue_diamond:
- Put the root into a queue
- Dequeue a node, process it and enqueue its children
- Top to bottom left to right traversal
- Queue is largest at the widest part of the tree, which is up to n/2 elements.
- O(n) memory use

**[Back to top :rocket:](#overview)**

--------------------------
--------------------------

# AVL TREES

## :star: AVL Properties :star:
- AVL trees are binary search trees with the AVL property
- AVL property: Balance = | height(left) – height(right) | can be at most 1
- Still must implement binary search
- Nodes in AVL trees have two extra fields: height and balance
- Trees with this condition still have O(log n) height
- No covering delete in this course. But know that lazy deletion is a thing (make a node as deleted and come back to it later) - log n 
- Find: O(log n)
- Insert O(log n) :triangular_flag_on_post: will be expected to insert like in all the practice problems
- If given the height, what are the min and max number of nodes? :question:

**Balanced AVL** |
------------ |
![alt text][balancedavl] |

--------------------------

## :star: AVL Rotations :star:
- AVL Rotations occur when an insertion makes a node out of balance. The rotation is performed at the lowest point of imbalance.
- The rotations are relative to the node that is unbalanced, with the rotation depending on which grandchild received the new node.
- Four types of rotations
  - Left-left and right-right rotations involve the child of the affected node being rotated up into position
  - Left-right and right-left rotations involve the grandchild being rotated up into position. The grandparent and parent become the two children.
- It is important that these rotations preserve BST property.

**Rotation** | **Example* |
-------- | --------- |
**Left-Left** | ![alt text][llavl] |
**Right-Right** | ![alt text][rravl] |
**Left-Right** | ![alt text][lravl] |
**Right-Left** | ![alt text][rlavl] |

**[Back to top :rocket:](#overview)**

--------------------------
--------------------------

# HASH TABLES

## :star: Properties :star:
- A large dataset M with a smaller set that should be saved, D
- A hash function maps M onto D
  - It should run in O(1) time
  - It should distribute into all of the available spots evenly
- Hash tables provide O(1) runtime IF
  - Collisions are not a problem
  - Decrease the chance of collisions by increasing the amount of memory (load factor)
    - Resizing is costly
- 2 ways to handle collisions
  1. Probing
    - Linear
    - Quadratic
    - Secondary Hashing
  2. Chaining

--------------------------

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

--------------------------

## :star: Chaining :star:
- Rather than probing for an open position, we could just save multiple objects in the same position
- Some data structure is necessary here
- Commonly: a linked list, AVL tree or secondary hash table.
- Resizing isn’t necessary, but if you don’t, you will get O(n) runtime.

**[Back to top :rocket:](#overview)**

--------------------------
--------------------------

# MEMORY HIERARCHY

## :star: Memory is not uniformly accessible :star:
- OS manages access to computer resources
- Some memory is on disk and some is in cache
- Dictated by two types of behavior
  - Spatial locality – Items near each other are moved together (memory pages)
  - Temporal locality – memory used recently will be used again

**[Back to top :rocket:](#overview)**

--------------------------
--------------------------

# B+-TREES

## :star: Properties :star:
- To reduce disk accesses we introduce the B-tree
- Two types of nodes
  - Signposts: Have M pointers and M-1 keys
  - Leaves: Have L <K,V> Pairs and a pointer to the next leaf
- Signposts must have at least M/2 pointers and leaves must have at least L/2 data points, unless it is the root
- Keys in signposts are the smallest item in the next pointer

--------------------------

## :star: Insert :star:
- Find the leaf that should hold the inserted element
- Insert the new k,v pair in sorted order in the leaf node
- If it overflows (i.e. the leaf is full when inserted)
  - Split the leaf into two nodes and add the new leaf to the parent
- If the signpost overflows, split the signpost into two signposts and try to add the new signpost to the parent
- Split back up to the root and create a new root if necessary

**[Back to top :rocket:](#overview)**

--------------------------
--------------------------

# HEAPS

## :star: Priority Queues ADT :star:
- Supports: insert(), findMin(), deleteMin(), changePriority()
- Data is stored in priority, value pairs
- In this class, we use the min-heap, where a lower value means it should dequeue first
- https://algs4.cs.princeton.edu/24pq/

--------------------------

## :star: Data Structure :star:

### :small_blue_diamond: Heap :small_blue_diamond:
- Complete binary tree
- complete binary tree with N nodes has exactly ceiling(N/2) leaf nodes
- Heap property
- [Visualizer](https://www.cs.usfca.edu/~galles/visualization/Heap.html)

### :small_blue_diamond: Implementation :small_blue_diamond:
- **Array**
  - fill in from review lecture
  - [How this works](https://algs4.cs.princeton.edu/24pq/images/heap-representations.png)
  - Why do an array at all?
    - Pros
      - Memory efficiency
      - Fast accesses to data (due to parent-child easy math, last position is index size)
      - Forces log n depth
    - Cons
      - Needs to resize
      - Can waste space (if tree is not complete???)

- **Find parents/children arithmetically**
  - You can put root at index 0, but this is not commonly done. Leaving index 0 empty and starting with root in index 1 is done for more conveneint index arithmatic. **This is an example of an [implementation decision](#star-implementation-star).**
  - Put the root of the array at index 1
  - Leave index 0 blank
  - Calculating children/parent becomes:
    - Left child: 2 * i
    - Right child: 2 * i + 1
    - Parent: i/2 
  - 

### :small_blue_diamond: Runtimes :small_blue_diamond: 
- Insert: O(log n), findMin: O(1), deleteMin O(log n)
- ChangePriority: O(log n)
- buildHeap, O(n)

--------------------------

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

--------------------------

## :star: Floyd’s method :star:
- For each element in the array from size/2 to the first element
- Percolate that element down as much as necessary
- Because most elements are near the bottom, they do not need to percolate down very far, this results in O(n) overall runtime

**[Back to top :rocket:](#overview)**

Perfect tree: Each row completely full
Full tree: Each node has 0 or 2 children
Complete tree: Each row completely full except maybe the bottom row,
which is filled from left to right

Beckman's Ale-gorithm - prof's algorithms prof's beer :beer:

Lazy delete for Sorted Array  
A general technique for making delete as fast as find: Instead of actually removing the item just mark it deleted

Plusses:  
- Simpler to delete (no shifting). If element is re-added soon afterward, simple to insert it again (no shifting)
- Can control removals and do them later in batches (amortized cost)

Minuses:  
- Extra space for the “is-it-deleted” flag
- Data structure full of deleted nodes wastes space
- Now we can’t use N in runtime: find O(log m) time where m is data-structure size (okay)


[sumof1ton]: https://github.com/kschumy/CSE373/raw/master/sumOfAllNumFrom1ToN.PNG  
[sumofpowersof2]: https://github.com/kschumy/CSE373/raw/master/sumOfPowersOf2.PNG    
[sumofinversepowersof2]: https://github.com/kschumy/CSE373/raw/master/sumOfInversePowersOf2.PNG  
[balancedavl]: https://github.com/kschumy/CSE373/raw/master/balancedAVL.PNG
[llavl]: https://github.com/kschumy/CSE373/raw/master/llAVL.PNG
[lravl]: https://github.com/kschumy/CSE373/raw/master/lrAVL.PNG
[rravl]: https://github.com/kschumy/CSE373/raw/master/rrAVL.PNG
[rlavl]: https://github.com/kschumy/CSE373/raw/master/rlAVL.PNG
