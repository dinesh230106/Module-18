# Ex. No: 18D - Travelling Salesman Problem (TSP)

## AIM:
To write a Python program to find the shortest possible route that visits every city exactly once and returns to the starting point using the **Travelling Salesman Problem (TSP)** approach.

## ALGORITHM:

**Step 1**: Start the program.

**Step 2**: Input the number of cities and the distance matrix.

**Step 3**: Set the starting city (e.g., city `0`).

**Step 4**: Generate all possible permutations of the remaining cities.

**Step 5**: For each permutation:
- Calculate the total cost of traveling through the permutation starting and ending at city `0`.
- Keep track of the **minimum cost** and the corresponding route.

**Step 6**: Return the **route** and the **minimum cost**.

**Step 7**: End the program.

## PYTHON PROGRAM

```
# Reg.No: 212223060057
# Name: DINESH KUMAR A
# Ex.No: 18D - Travelling Salesman Problem (TSP)

from itertools import permutations

def tsp(distance_matrix):
    n = len(distance_matrix)
    cities = list(range(n))
    start = 0
    min_cost = float('inf')
    best_route = []

    # Generate all permutations of cities excluding the starting city
    for perm in permutations(cities[1:]):
        cost = 0
        route = [start] + list(perm) + [start]
        for i in range(n):
            cost += distance_matrix[route[i]][route[i+1]]
        if cost < min_cost:
            min_cost = cost
            best_route = route

    print(f"Optimal route: {best_route}")
    print(f"Minimum travel cost: {min_cost}")

# Example Usage
distance_matrix = [
    [0, 10, 15, 20],
    [10, 0, 35, 25],
    [15, 35, 0, 30],
    [20, 25, 30, 0]
]

tsp(distance_matrix)

```

## OUTPUT
```
Optimal route: [0, 1, 3, 2, 0]
Minimum travel cost: 80

```

## RESULT
The program successfully finds the shortest route visiting all cities exactly once and returning to the starting city, demonstrating a solution to the Travelling Salesman Problem.


