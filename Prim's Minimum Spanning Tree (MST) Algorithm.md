# Ex. No: 18A - Prim's Minimum Spanning Tree (MST) Algorithm

## AIM:
To write a Python program for **Prim's Minimum Spanning Tree (MST)** algorithm.

## ALGORITHM:

**Step 1**: Initialize the `key[]` array to infinity, set the first vertex's key to `0`, and create `mstSet[]` and `parent[]` arrays.

**Step 2**: Select the vertex with the smallest key value not yet included in `mstSet`.

**Step 3**: Add the selected vertex to `mstSet`.

**Step 4**: For all adjacent vertices:
- If the edge weight is smaller than their current key value, and the vertex is not in `mstSet`, then:
  - Update their key value
  - Update their parent to the current vertex

**Step 5**: Repeat Steps 2–4 until all vertices are included in the MST.

**Step 6**: Print the resulting Minimum Spanning Tree using the `parent[]` array.

## PYTHON PROGRAM

```
# Reg.No: 212223060057
# Name: DINESH KUMAR A
# Ex.No: 18A - Prim's Minimum Spanning Tree Algorithm

import sys

def prim_mst(graph):
    V = len(graph)
    key = [sys.maxsize] * V  # Initialize all keys as infinite
    parent = [None] * V      # Array to store MST
    key[0] = 0               # Start from vertex 0
    mstSet = [False] * V

    for _ in range(V):
        # Pick the minimum key vertex not yet included
        min_key = sys.maxsize
        u = -1
        for v in range(V):
            if key[v] < min_key and not mstSet[v]:
                min_key = key[v]
                u = v

        mstSet[u] = True

        # Update key and parent for adjacent vertices
        for v in range(V):
            if graph[u][v] > 0 and not mstSet[v] and graph[u][v] < key[v]:
                key[v] = graph[u][v]
                parent[v] = u

    print("Edge \tWeight")
    total_weight = 0
    for i in range(1, V):
        print(f"{parent[i]} - {i} \t{graph[i][parent[i]]}")
        total_weight += graph[i][parent[i]]
    print(f"Total weight of MST: {total_weight}")


# Example Usage
graph = [
    [0, 2, 0, 6, 0],
    [2, 0, 3, 8, 5],
    [0, 3, 0, 0, 7],
    [6, 8, 0, 0, 9],
    [0, 5, 7, 9, 0]
]

prim_mst(graph)

```

## OUTPUT

```
Edge 	Weight
0 - 1 	2
1 - 2 	3
0 - 3 	6
1 - 4 	5
Total weight of MST: 16

```


## RESULT
The program successfully finds the Minimum Spanning Tree (MST) using Prim's algorithm, displaying all included edges and the total minimum cost.


