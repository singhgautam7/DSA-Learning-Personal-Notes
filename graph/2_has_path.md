# Has Path
Write a function, has_path, that takes in a dictionary representing the adjacency list of a directed acyclic graph and two nodes (src, dst). The function should return a boolean indicating whether or not there exists a directed path between the source and destination nodes.

**test_00:**
```python
graph = {
  'f': ['g', 'i'],
  'g': ['h'],
  'h': [],
  'i': ['g', 'k'],
  'j': ['i'],
  'k': []
}

has_path(graph, 'f', 'k') # True
```

## Solution
### Recursive DFS
```python
def has_path(graph, src, dst):
    # If source == destination, return True
    if src == dst:
        return True

    # Loop through the neighbors
    for neighbor in graph[src]:

        # Recursive call with the current neighbor as source
        if has_path(graph, neighbor, dst):

        # Pass the True upwards
        return True

    return False
```
n = number of nodes
e = number edges
Time: O(e)
Space: O(n)

### BFS
```python
from collections import deque

def has_path(graph, src, dst):
    queue = deque([ src ])

    while queue:
        current = queue.popleft()

        if current == dst:
            return True

    for neighbor in graph[current]:
        queue.append(neighbor)

    return False
```
n = number of nodes
e = number edges
Time: O(e)
Space: O(n)