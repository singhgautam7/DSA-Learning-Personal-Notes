# Linked List Find

Write a function, linked_list_find, that takes in the head of a linked list and a target value. The function should return a boolean indicating whether or not the linked list contains the target. You have a class Node is defined as follows -
```python
class Node:
  def __init__(self, val):
    self.val = val
    self.next = None
```

**test_00:**
```python
a = Node("a")
b = Node("b")
c = Node("c")
d = Node("d")

a.next = b
b.next = c
c.next = d

# a -> b -> c -> d

linked_list_find(a, "c") # True
```

## Solution
### Iterative
```python
def linked_list_find(head, target):
  current = head
  while current is not None:
    if current.val == target:
      return True
    current = current.next
  return False
```

### Recursive
```python
def linked_list_find(head, target):
  if head is None:
    return False
  if head.val == target:
    return True
  return linked_list_find(head.next, target)
```