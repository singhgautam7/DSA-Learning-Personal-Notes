# Tree Min Value
Write a function, tree_min_value, that takes in the root of a binary tree that contains number values. The function should return the minimum value within the tree.
You may assume that the input tree is non-empty. You have the following Node class
```python
class Node:
  def __init__(self, val):
    self.val = val
    self.left = None
    self.right = None
```

**test_00:**
```python
a = Node(3)
b = Node(11)
c = Node(4)
d = Node(4)
e = Node(-2)
f = Node(1)

a.left = b
a.right = c
b.left = d
b.right = e
c.right = f

#       3
#    /    \
#   11     4
#  / \      \
# 4   -2     1
tree_min_value(a) # -> -2
```

**test_01:**
```python
a = Node(5)
b = Node(11)
c = Node(3)
d = Node(4)
e = Node(14)
f = Node(12)

a.left = b
a.right = c
b.left = d
b.right = e
c.right = f

#       5
#    /    \
#   11     3
#  / \      \
# 4   14     12

tree_min_value(a) # -> 3
```
## Solution

### Depth First Recursive
```python
def tree_min_value(root):
  if root is None:
    return float("inf")
  smallest_left_value = tree_min_value(root.left)
  smallest_right_value = tree_min_value(root.right)
  return min(root.val, smallest_left_value, smallest_right_value)
```
- n = number of nodes
- Time: O(n)
- Space: O(n)

### Depth First Iterative
```python
def tree_min_value(root):
  stack = [ root ]
  smallest = float("inf")
  while stack:
    current = stack.pop()
    if current.val < smallest:
      smallest = current.val

    if current.left is not None:
      stack.append(current.left)
    if current.right is not None:
      stack.append(current.right)

  return smallest
```
- n = number of nodes
- Time: O(n)
- Space: O(n)

### Breadth First Iterative
```python
from collections import deque

def tree_min_value(root):
  queue = deque([ root ])
  smallest = float("inf")
  while queue:
    current = queue.popleft()
    if current.val < smallest:
      smallest = current.val

    if current.left is not None:
      queue.append(current.left)
    if current.right is not None:
      queue.append(current.right)

  return smallest
```
- n = number of nodes
- Time: O(n)
- Space: O(n)

