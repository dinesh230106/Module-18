# Ex. No: 18C - Dijkstra's Single Source Shortest Path Algorithm

## AIM:
To write a Python program for **Dijkstra's single source shortest path algorithm**.

## ALGORITHM:

**Step 1**: Initialize a `distance[]` array with infinity for all vertices except the source, which is set to `0`.  
Create a `sptSet[]` array (shortest path tree set) to keep track of vertices whose shortest distance from the source is finalized.

**Step 2**: Pick the vertex `u` with the minimum distance value from the set of vertices not yet processed.

**Step 3**: For every adjacent vertex `v` of the picked vertex `u`, if the current distance to `v` is greater than the distance to `u` plus the edge weight `(u, v)`, then update the distance of `v`.

**Step 4**: Mark the vertex `u` as processed in `sptSet`.

**Step 5**: Repeat Steps 2–4 until all vertices are processed.

**Step 6**: Print the shortest distances from the source to all other vertices.

## PYTHON PROGRAM

```
# Reg.No: 212223060057
# Name: DINESH KUMAR A
# Ex.No: 18C - Dijkstra's Single Source Shortest Path Algorithm

import sys

def min_distance(dist, sptSet, V):
    min_val = sys.maxsize
    min_index = -1
    for v in range(V):
        if dist[v] < min_val and not sptSet[v]:
            min_val = dist[v]
            min_index = v
    return min_index

def dijkstra(graph, src):
    V = len(graph)
    dist = [sys.maxsize] * V
    dist[src] = 0
    sptSet = [False] * V

    for _ in range(V):
        u = min_distance(dist, sptSet, V)
        sptSet[u] = True
        for v in range(V):
            if (graph[u][v] > 0 and not sptSet[v] and
                dist[u] + graph[u][v] < dist[v]):
                dist[v] = dist[u] + graph[u][v]

    print("Vertex \tDistance from Source")
    for i in range(V):
        print(f"{i} \t {dist[i]}")

# Example graph represented as an adjacency matrix
graph = [
    [0, 4, 0, 0, 0, 0, 0, 8, 0],
    [4, 0, 8, 0, 0, 0, 0, 11, 0],
    [0, 8, 0, 7, 0, 4, 0, 0, 2],
    [0, 0, 7, 0, 9, 14, 0, 0, 0],
    [0, 0, 0, 9, 0, 10, 0, 0, 0],
    [0, 0, 4, 14, 10, 0, 2, 0, 0],
    [0, 0, 0, 0, 0, 2, 0, 1, 6],
    [8, 11, 0, 0, 0, 0, 1, 0, 7],
    [0, 0, 2, 0, 0, 0, 6, 7, 0]
]

# Source vertex
source = 0
dijkstra(graph, source)

```

## OUTPUT
```
Vertex 	Distance from Source
0 	 0
1 	 4
2 	 12
3 	 19
4 	 21
5 	 11
6 	 9
7 	 8
8 	 14

```

## RESULT
The program successfully computes the shortest distances from a given source vertex to all other vertices using Dijkstra’s algorithm.
