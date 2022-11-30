# Zipper List
Write a function, zipper_lists, that takes in the head of two linked lists as arguments. The function should zipper the two lists together into single linked list by alternating nodes. If one of the linked lists is longer than the other, the resulting list should terminate with the remaining nodes. The function should return the head of the zippered linked list.

Do this in-place, by mutating the original Nodes.

You may assume that both input lists are non-empty.

**test_00:**
```python
a = Node("a")
b = Node("b")
c = Node("c")
a.next = b
b.next = c
# a -> b -> c

x = Node("x")
y = Node("y")
z = Node("z")
x.next = y
y.next = z
# x -> y -> z

zipper_lists(a, x)
# a -> x -> b -> y -> c -> z
```

**test_02:**
```python
s = Node("s")
t = Node("t")
s.next = t
# s -> t

one = Node(1)
two = Node(2)
three = Node(3)
four = Node(4)
one.next = two
two.next = three
three.next = four
# 1 -> 2 -> 3 -> 4

zipper_lists(s, one)
# s -> 1 -> t -> 2 -> 3 -> 4
```

**test_03:**
```python
w = Node("w")
# w

one = Node(1)
two = Node(2)
three = Node(3)
one.next = two
two.next = three
# 1 -> 2 -> 3

zipper_lists(w, one)
# w -> 1 -> 2 -> 3
```

**test_04:**
```python
one = Node(1)
two = Node(2)
three = Node(3)
one.next = two
two.next = three
# 1 -> 2 -> 3

w = Node("w")
# w

zipper_lists(one, w)
# 1 -> w -> 2 -> 3
```

## Solution
### Iterative
```python
def zipper_lists(head_1, head_2):
    tail = head_1
    current_1 = head_1.next
    current_2 = head_2
    count = 0

    # Loop till one of the current becomes None
    while current_1 is not None and current_2 is not None:

        # If even, take from list 2
        if count % 2 == 0:
        tail.next = current_2
        current_2 = current_2.next

        # Else, take from list 1
        else:
        tail.next = current_1
        current_1 = current_1.next

        # Move the tail to one node ahead, and also increase the count
        tail = tail.next
        count += 1

    # If even after the loop, there still remains any list,
    #  directly append them to tail end
    if current_1 is not None:
        tail.next = current_1
    if current_2 is not None:
        tail.next = current_2

    return head_1
```
- n = length of list 1
- m = length of list 2
- Time: O(min(n, m))
- Space: O(1)

### Recursive
```python
def zipper_lists(head_1, head_2):
    if head_1 is None and head_2 is None:
        return None
    if head_1 is None:
        return head_2
    if head_2 is None:
        return head_1
    next_1 = head_1.next
    next_2 = head_2.next
    head_1.next = head_2
    head_2.next = zipper_lists(next_1, next_2)
    return head_1
```
- n = length of list 1
- m = length of list 2
- Time: O(min(n, m))
- Space: O(min(n, m))