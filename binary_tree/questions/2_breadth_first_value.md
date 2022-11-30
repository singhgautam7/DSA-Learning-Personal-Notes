# Breadth first values
Write a function, breadth_first_values, that takes in the root of a binary tree. The function should return a list containing all values of the tree in breadth-first order. You have the following Node class
```python
class Node:
  def __init__(self, val):
    self.val = val
    self.left = None
    self.right = None
```

**test_00:**
```python
a = Node('a')
b = Node('b')
c = Node('c')
d = Node('d')
e = Node('e')
f = Node('f')

a.left = b
a.right = c
b.left = d
b.right = e
c.right = f

#      a
#    /   \
#   b     c
#  / \     \
# d   e     f

breadth_first_values(a)
#    -> ['a', 'b', 'c', 'd', 'e', 'f']
```

**test_01:**
```python
a = Node('a')
b = Node('b')
c = Node('c')
d = Node('d')
e = Node('e')
f = Node('f')
g = Node('g')
h = Node('h')

a.left = b
a.right = c
b.left = d
b.right = e
c.right = f
e.left = g
f.right = h

#      a
#    /   \
#   b     c
#  / \     \
# d   e     f
#    /       \
#   g         h

breadth_first_values(a)
#   -> ['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']
```

**test_02:**
```python
breadth_first_values(None)
#    -> []
```


## Solution

```python
from collections import deque

def breadth_first_values(root):
    if not root:
        return []

    values = []
    queue = deque([root])

    # While there are still some items in queue
    while queue:

        # Take the first entered element and push it to result
        current = queue.popleft()
        values.append(current.val)

        # Check the left child first to add to the queue so that the left is popped first
        if current.left:
            queue.append(current.left)

        if current.right:
            queue.append(current.right)

    return values
```
- n = number of nodes
- Time: O(n)
- Space: O(n)