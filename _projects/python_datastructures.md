---
layout: page
title: Python Datastructures
description: Collection of self-implemented datastructure with python, including a Queue, Stack, BST, Hashmap, LL, Heap...
img: assets/img/python_datastructures.jpg
importance: 1
category: Algorithms / Datastructures
related_publications: false
---

#### Source code

<a href="https://github.com/GeoffreyKarnbach/Python-Datastructures">Go to the GitHub repository!</a>

#### Requirements

The datastructures can be used with any datatype.
<br><br>
Basic requirements for datatypes:

- Can be compared with == , < , > (Necessary only for the Binary Search Tree)
- Have a way to be displayed properly (for instance for classes through the \_\_str\_\_ method)

#### Datastructures:

- [Stack](#stack)
- [Queue](#queue)
- [Double Ended Queue](#dequeue)
- [Dictionary / Associative Structure](#dictionary)
- [Linked List](#linked-list)
- [Binary Search Tree](#binary-search-tree)
- [Hashmap](#hashmap)
- [Hashlist](#hashlist)
- [Heap = Priority Queue](#heap)

<br>
For further reference, the Wikipedia list of some data structures:

https://en.wikipedia.org/wiki/List_of_data_structures

#### <u>Documentation</u>

#### <a id="stack"></a><u>Stack</u>

https://en.wikipedia.org/wiki/Stack_(abstract_data_type)

Stacks work with the LIFO system: Last In First Out.

```python
from stack import*

s = Stack()

for loop in range(1,10):
    s.push(loop)

print(s) #Works properly as long as elements in stack have __str__ method

while s.size() > 0:
    print(s.pop()) #Numbers from 9 to 1

print(s.pop()) #None
```

Available methods:

- push(value) -> adds value to the end
- pop() -> returns last value and deletes it
- peek() -> returns last value
- size() -> returns size of stack

The constructor has to stay empty, no starting data needs to be passed.

#### <a id="queue"></a><u>Queue</u>

https://en.wikipedia.org/wiki/Queue_(abstract_data_type)

Queues work with the FIFO system: First In First Out.

```python
from queue import*

q = Queue()

for loop in range(1,10):
    q.add(loop)

while q.size() > 0:
    print(q.poll()) #Numbers from 1 to 9

print(q.peek()) #None
```

Available methods:

- add(value) -> adds value to the end
- poll() -> returns first value and deletes it
- peek() -> returns first value
- size() -> returns size of queue

The constructor has to stay empty, no starting data needs to be passed.

#### <a id="dequeue"></a><u>Double Ended Queue <=> DEQUEUE</u>

https://en.wikipedia.org/wiki/Double-ended_queue

The Double Ended Queue is a mix of the stack and the queue and can therefore be used instead of those structures.

```python
from dequeue import*

dq = Dequeue()

for loop in range(1,10):
    dq.addLast(loop)

while dq.size() > 0:
    print(dq.pollFirst()) #Numbers from 1 to 9

print(dq.pollFirst()) #None
```

Available methods:

- addFirst(value) -> adds value to the beginning
- addLast(value) -> adds value to the end
- pollFirst() -> returns first value and deletes it
- pollLast() -> returns last value and deletes it
- peekFirst() -> returns first value
- peekLast() -> returns last value
- size() -> returns size of dequeue

#### <a id="dictionary"></a><u>Dictionary</u>

https://en.wikipedia.org/wiki/Associative_array

The "dictionary", also known as associative structure or array, is similar to the built-in dictionary in python.

```python
from dictionary import*

assoc = Dictionary()

print(assoc.put("France", "Pari"))#None
print(assoc.put("Germany", "Berlin"))#None
print(assoc.put("Austria", "Vienna"))#None

print(assoc)

print(assoc.put("France", "Paris")) #Pari
print(assoc.remove("England")) #None
print(assoc.remove("Germany")) #Berlin

print(assoc)

print(assoc.containsKey("England"))#False
print(assoc.containsKey("France"))#True

print(assoc.containsValue("London"))#False
print(assoc.containsValue("Paris"))#True

print(assoc.size())#2
```

Available methods:

- put(key, value) -> adds the key-value pair or updates the value (returning old value)
- get(key) -> returns corresponding value for given key
- remove(key) -> removes the given key-value pair and returns it
- containsKey(key) -> returns true/false
- containsValue(value) -> returns true/false
- size() -> return number of key-value pairs

#### <a id="linked-list"></a><u>Linked List</u>

https://en.wikipedia.org/wiki/Linked_list

```python
from linkedlist import*

ll = LinkedList()

ll.addLast(1)
ll.addLast(2)
ll.addLast(3)
ll.addLast(4)

print(ll.getFirst()) #1
print(ll.getLast()) #4

for loop in range(ll.size()):
    print(ll.get(loop)) #1 to 4

print(ll.pollFirst()) #1

print(ll)
```

Available methods:

- constructor(head: ListNode) -> Constructor with option to pass first Node, has to be a **ListNode**
- add(value, i) -> adds the given value to a ListNode inserted at position i
- addFirst(value) -> adds the given value to a ListNode in first position
- addLast(value) -> adds the given value to a ListNode in last position
- get(i) -> returns value at index i
- getFirst() -> returns value of "head" node
- getLast() -> returns value of last node
- pollFirst() -> returns value of head node and removes it
- pollLast() -> returns value of last node and removes it
- indexOf(value) -> returns index of given value or -1 if not found
- size() -> returns amount of Nodes in LinkedList

#### <a id="binary-search-tree"></a><u>Binary Search Tree</u>

https://en.wikipedia.org/wiki/Binary_search_tree

WIP: Better representation of the BST through the str() method<br>
WIP: Add remove function for BST

- BST: Each Treenode has left and right child
- Key of left child always smaller then parent
- Key of right child always bigger then parent

```python
from binarysearchtree import*

bst = BinarySearchTree()

bst.put(5,10)
bst.put(2,4)
bst.put(7,14)
bst.put(1,2)
bst.put(3,6)

print(bst.get(6)) #None
print(bst.get(2)) #4
print(bst.contains(10)) #False

print(bst)
```

Available methods:

- put(key, value) -> adds key-value pair to BST
- get(key) -> returns the associated value with key or None
- contains(key) -> returns True/False if key is in BST <=> get(key) != None

Usage of an internal "helper" class: Treenode (further documentation in source code)

#### <a id="hashmap"></a><u>Hashmap / Hashtable</u>

https://en.wikipedia.org/wiki/Hash_table

The Hashmap is similar to the associative structure but doesn't use a linear search to find elements inside of it, but computes the index with the object hash and in relation to the internal array size.

```python
from hashmap import*

hm = Hashmap()

for loop in range(16):
    hm.put(loop, loop*2)

print(hm)

for loop in range(16):
    print(str(loop) + " => " + str(hm.get(loop)))

print()

print(hm.containsKey(10)) #True
print(hm.containsKey(18)) #False

hm.remove(10)

print(hm)

print(hm.containsKey(10)) #False
```

Available methods:

- index(value) -> returns index that value would have in hashmap (internal method)
- put(key, value) -> inserts or updates the value for the given key, and returns old value or None
- get(key) -> returns the value that is associated to the key or None
- containsKey(key) -> returns True/False if key is in the hashmap
- remove(key) -> removes the key/value pair from hashmap and returns True if key was removed (or False if not found)

#### <a id="hashlist"></a><u>Hashlist</u>

https://en.wikipedia.org/wiki/Hash_list

A Hashlist is similar to a Hashmap but without the usage of a value associated to a key. Hashlistes can be used, for instance, to check in constant lookup time if an element exists.

```python

from hashlist import*

hl = Hashlist()

hl.put("Python")
hl.put("C++")
hl.put("Java")

toCheck = ["Python","C++","C#","Java"]

for item in toCheck:
    print(f"Element {item} in hashlist: {hl.contains(item)}") #True,True,False,True

print(hl.remove("Java"))#True

print(hl)

```

Available methods:

- index(value) -> returns index that value would have in hashlist
- put(value) -> adds value to hashlist
- contains(value) -> returns True/False if value in hashlist
- remove(value) -> removes value from hashlist and returns if something has been removed

#### <a id="heap"></a><u>Heap / Priority Queue</u>

https://en.wikipedia.org/wiki/Priority_queue

A Heap or Priority Queue is a structure to save different "tasks", each having a priority value (higher is more urgent) and an optional description. Priority Queues can be used to organize work and to deal with tasks that are more urgent. It can also be used to reduce the time complexity for algorithms (for instance Dijkstra Algorithm), because the operations on a Heap are in O(log n).

```python

from heap import*

hp = Heap()

hp.put(1)
hp.put(6,"Prio 6")
hp.put(10,"Prio 10")
hp.put(5,"Prio 5")
hp.put(8,"Prio 8")

print(hp)

while hp.size() > 0:
    print(hp.get()) #10 - 8 - 6 - 5 - 1

print(hp.get()) #None
```

Available methods:

- heapify(position) -> restores the heap condition for the index position and works up recursively
- heapifier() -> internal method to call all necessary "heapify() calls" to make sure that the heap condition is met again
- put(value) -> inserts value into the priority queue
- delete(positon) -> removes the element at position and restores heap condition with heapify
- get() -> returns item with highest priority (index 0) and deletes it


