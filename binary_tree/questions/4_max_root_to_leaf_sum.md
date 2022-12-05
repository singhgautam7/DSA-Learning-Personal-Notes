# Max root to leaf path sum
Write a function, max_path_sum, that takes in the root of a binary tree that contains number values. The function should return the maximum sum of any root to leaf path within the tree. You may assume that the input tree is non-empty. You have the following Node class
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

max_path_sum(a) # -> 18
```

**test_01:**
```python
a = Node(5)
b = Node(11)
c = Node(54)
d = Node(20)
e = Node(15)
f = Node(1)
g = Node(3)

a.left = b
a.right = c
b.left = d
b.right = e
e.left = f
e.right = g

#        5
#     /    \
#    11    54
#  /   \
# 20   15
#      / \
#     1  3

max_path_sum(a) # -> 59
```
## Solution

### Depth First Recursive
```python
def max_path_sum(root):
    # If any recursive node is None
    if root is None:
        return float('-inf')

    # If root node is the leaf node
    if root.left is None and root.right is None:
        return root.val

    # Getting the sum of left and right path
    max_left = max_path_sum(root.left)
    max_right = max_path_sum(root.right)

    # Return sum of root, and max of left and right
    return root.val + max(max_left, max_right)
```
- n = number of nodes
- Time: O(n)
- Space: O(n)
