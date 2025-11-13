# Ex. No: 18E - Count the Number of Triangles in an Undirected Graph

## AIM:
To write a Python program to **count the number of triangles** present in an **undirected graph** using matrix operations.

## ALGORITHM:

**Step 1**: Initialize a matrix `aux2` to store the square of the adjacency matrix (i.e., `graph²`).  
Also, initialize a matrix `aux3` to store the cube of the adjacency matrix (i.e., `graph³`).

**Step 2**: Multiply the adjacency matrix with itself to compute `aux2 = graph × graph`.

**Step 3**: Multiply `aux2` with the adjacency matrix again to compute `aux3 = aux2 × graph`.

**Step 4**: Compute the **trace** of the matrix `aux3` (i.e., the sum of diagonal elements of the matrix).

**Step 5**: Divide the trace by **6** to get the number of triangles in the graph.  
*(Each triangle is counted six times in the trace — twice per vertex and once per direction.)*

**Step 6**: Return the result.

## PYTHON PROGRAM

```
# Reg.No: 212223060057
# Name: DINESH KUMAR A
# Ex.No: 18E - Count the Number of Triangles in an Undirected Graph

import numpy as np

def count_triangles(graph):
    # Convert graph to numpy array if not already
    G = np.array(graph)
    
    # Compute graph squared and cubed
    aux2 = np.matmul(G, G)
    aux3 = np.matmul(aux2, G)
    
    # Trace of aux3
    trace = np.trace(aux3)
    
    # Each triangle is counted 6 times
    num_triangles = trace // 6
    return int(num_triangles)

# Example adjacency matrix for an undirected graph
graph = [
    [0, 1, 1, 0],
    [1, 0, 1, 1],
    [1, 1, 0, 1],
    [0, 1, 1, 0]
]

print("Number of triangles in the graph:", count_triangles(graph))

```

## OUTPUT
```
Number of triangles in the graph: 2

```

## RESULT
The program successfully calculates and displays the number of triangles in an undirected graph using matrix multiplication.
