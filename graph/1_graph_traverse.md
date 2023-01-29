# Example graph
```python
graph = {
    "a": ["b", "c"],
    "b": ["d"],
    "c": ["e"],
    "d": ["f"],
    "e": [],
    "f": [],
}
```
> Note: Goal is to traverse and print the nodes

# Depth First search
## Brute force
```python
def dps(graph, start):
    stack = [start]
    while stack:
        current = stack.pop()
        print(current)
        for neighbor in graph[current]:
            stack.append(neighbor)
```

## Recursive
```python
def dps(graph, current):
    print(current)
    for neighbor in graph[current]:
        dps(graph, neighbor)
```

# Breadth First search
## Brute force
```python
from collections import deque
def bfs(graph, start):
    queue = deque([start])
    while queue:
        current = queue.popleft()
        print(current)
        for neighbor in graph[current]:
            queue.append(neighbor)
```

## Recursive
```python
def bfs(graph, current):
    print(current)
    for neighbor in graph[current]:
        bfs(graph, neighbor)
```