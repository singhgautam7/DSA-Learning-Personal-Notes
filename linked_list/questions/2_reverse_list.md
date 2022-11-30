# Reverse List
Write a function, reverse_list, that takes in the head of a linked list as an argument. The function should reverse the order of the nodes in the linked list in-place and return the new head of the reversed linked list. You have a class Node is defined as follows -
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
e = Node("e")
f = Node("f")

a.next = b
b.next = c
c.next = d
d.next = e
e.next = f

# a -> b -> c -> d -> e -> f

reverse_list(a) # f -> e -> d -> c -> b -> a
```

## Solution
### Iterative
```python
def reverse_list(head):
    prev = None
    current = head
    while current is not None:
        next = current.next
        current.next = prev
        prev = current
        current = next
    return prev
```
- n = number of nodes
- Time: O(n)
- Space: O(1)

### Recursive
```python
def reverse_list(head, prev = None):
    if head is None:
        return prev
    next = head.next
    head.next = prev
    return reverse_list(next, head)
```

- n = number of nodes
- Time: O(n)
- Space: O(n)
