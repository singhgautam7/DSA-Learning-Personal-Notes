# Depth first values
Write a function, depth_first_values, that takes in the root of a binary tree. The function should return a list containing all values of the tree in depth-first order. You have the following Node class
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

depth_first_values(a)
#   -> ['a', 'b', 'd', 'e', 'c', 'f']
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
a.left = b
a.right = c
b.left = d
b.right = e
c.right = f
e.left = g

#      a
#    /   \
#   b     c
#  / \     \
# d   e     f
#    /
#   g

depth_first_values(a)
#   -> ['a', 'b', 'd', 'e', 'g', 'c', 'f']
```

**test_02:**
```python
depth_first_values(None)
#   -> []
```


## Solution

```python
# class Node:
#   def __init__(self, val):
#     self.val = val
#     self.left = None
#     self.right = None

def depth_first_values(root):
    if root is None:
        return []

    values = []
    stack = [root]

    # While there are still some items in stack
    while stack:

        # Take the top most element and push it to the result
        current = stack.pop()
        values.append(current.val)

        # Check the right child first to add to stack so that left is popped first
        if current.right is not None:
        stack.append(current.right)
        if current.left is not None:
        stack.append(current.left)

    return values
```
- n = number of nodes
- Time: O(n)
- Space: O(n)