
# BREADTH-FIRST-SEARCH

<h1>ExpNo 3: Implement Breadth First Search Traversal of a Graph</h1>

<h3>Name: K RAGAPRIYAN</h3>
<h3>Register Number: 212225040323</h3>

<h3>Aim:</h3>

To implement Breadth First Search Traversal of a Graph using Python 3.

<h3>Theory:</h3>

Breadth-First Traversal (or Search) for a graph is like the Breadth-First Traversal of a tree. The only catch here is that, unlike trees, graphs may contain cycles, so we may come to the same node again. To avoid processing a node more than once, we divide the vertices into two categories:

1. Visited
2. Not Visited

A Boolean visited array is used to mark the visited vertices. For simplicity, it is assumed that all vertices are reachable from the starting vertex. BFS uses a queue data structure for traversal.

<strong>How does BFS work?</strong>

Starting from the root, all the nodes at a particular level are visited first, and then the next-level nodes are traversed until all the nodes are visited.

To do this, a queue is used. All the adjacent unvisited nodes of the current level are pushed into the queue, and the current-level nodes are marked visited and popped from the queue.

### Illustration:

Let us understand the working of the algorithm with the help of the following example.

**Step 1:** Initially, the queue and visited arrays are empty.

![Step 1](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8acdebf8-ecc2-4d10-a208-45cce441f059)

Queue and visited arrays are empty initially.

**Step 2:** Push node 0 into the queue and mark it as visited.

![Step 2](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/0e9ce012-8e1f-43d7-b7b9-c0fb19fe0c3f)

Push node 0 into the queue and mark it as visited.

**Step 3:** Remove node 0 from the front of the queue, visit its unvisited neighbours, and push them into the queue.

![Step 3](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/67d8fa3b-ce9e-46c2-9dd7-089e204e667a)

**Step 4:** Remove node 1 from the front of the queue, visit its unvisited neighbours, and push them into the queue.

![Step 4](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/b0cf0fde-8a86-41cb-a054-36875ac24ab0)

**Step 5:** Remove node 2 from the front of the queue, visit its unvisited neighbours, and push them into the queue.

![Step 5](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8968a163-6b3a-4f7e-8ad4-bbf24f326b9b)

**Step 6:** Remove node 3 from the front of the queue, visit its unvisited neighbours, and push them into the queue.

As we can see, all the neighbours of node 3 have been visited, so we move to the next node at the front of the queue.

![Step 6](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/7a1c1b16-ea69-497f-a099-8440200f6dc0)

**Step 7:** Remove node 4 from the front of the queue, visit its unvisited neighbours, and push them into the queue.

As we can see, all the neighbours of node 4 have been visited, so we move to the next node at the front of the queue.

![Step 7](https://github.com/natsaravanan/19AI405FUNDAMENTALSOFARTIFICIALINTELLIGENCE/assets/87870499/8e16ffa3-c3d6-4774-822b-6eb84adedad9)

Remove node 4 from the front of the queue and visit its unvisited neighbours.

Now, the queue becomes empty, so the iteration process is terminated.

---

<h2>Algorithm:</h2>

1. Construct a graph with nodes and edges.
2. Breadth First Search uses a queue and iterates through it for traversal.
3. Insert a starting node into the queue.
4. Find its successors or neighbours and check whether each node has been visited.
5. If a node has not been visited, add it to the queue. Otherwise, continue.
6. Repeat steps 4 and 5 until all nodes have been visited and there are no more unvisited nodes.

---

<h2>Python Program:</h2>

```python
from collections import deque

# Read the number of vertices and edges
n, e = map(int, input().split())

# Create an empty graph
graph = {}

# Read the edges and construct the graph
for _ in range(e):
    u, v = input().split()

    if u not in graph:
        graph[u] = []

    if v not in graph:
        graph[v] = []

    graph[u].append(v)
    graph[v].append(u)


# Breadth First Search function
def bfs(start):
    visited = set()
    queue = deque()

    # Insert the starting node into the queue
    queue.append(start)
    visited.add(start)

    result = []

    # Traverse the graph
    while queue:
        node = queue.popleft()
        result.append(node)

        # Visit all adjacent nodes
        for neighbour in graph[node]:
            if neighbour not in visited:
                visited.add(neighbour)
                queue.append(neighbour)

    return result


# Start BFS from the first inserted vertex
start = next(iter(graph))

# Display the BFS traversal
print(bfs(start))
```

---

<h2>Sample Input 1:</h2>

```text
7 9
A B
A C
A F
C E
C F
C D
D E
D G
G F
```

<h2>Sample Output 1:</h2>

```text
['A', 'B', 'C', 'F', 'E', 'D', 'G']
```

<h3>Output 1 - Screenshot</h3>

![Output 1](<Screenshot 2026-11-23 140056.png>)

---

<h2>Sample Input 2:</h2>

```text
5 6
0 1
0 2
1 2
1 3
2 4
3 4
```

<h2>Sample Output 2:</h2>

```text
['0', '1', '2', '3', '4']
```

<h3>Output 2 - Screenshot</h3>

![Output 2](<Screenshot 2026-11-23 140747.png>)

---

<h3>Result:</h3>

Thus, a graph was constructed and the implementation of Breadth First Search for the same graph was completed successfully.
