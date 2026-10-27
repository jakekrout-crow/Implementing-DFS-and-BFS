# Assignment: Implementing DFS and BFS

## Introduction

In this assignment, you will implement a `Graph` class with methods for depth-first search (DFS) and breadth-first search (BFS), along with utility methods for solving network analysis problems. You'll then test your implementation using a provided starter file.

### Starter Files

The starter file contains the following:
1. A `PerformanceAnalyzer` class to measure execution time and memory usage.
2. A `run_tests()` function to benchmark and validate your implementation.

Download the starter file from your course repository and use it to test your `Graph` class.

## Learning Outcomes

By completing this assignment, you will:

1. Implement a graph structure with methods for DFS and BFS traversal.
2. Solve problems such as finding connected components, determining distances, and identifying shortest paths.
3. Analyze and compare the performance of DFS and BFS in terms of execution time and memory usage.

## Instructions

### Problem Context

You are tasked with analyzing a network represented as an undirected graph. Nodes represent entities (e.g., people, devices), and edges represent relationships or connections between them. Your goal is to implement the following functionalities:

- Add nodes and edges to represent the graph.
- Perform graph traversal using both DFS (recursive and iterative) and BFS.
- Implement utility methods for:
   - Finding all nodes within `n` connections from a given node.
   - Checking if two nodes are connected.
   - Finding the shortest path between two nodes.

## Implementation Requirements

#### Graph Class
Implement the `Graph` class with the following methods:

**Graph Construction**:

- `add_node(node: int) -> None`: Add a node to the graph if it doesn’t already exist.
- `add_edge(node1: int, node2: int) -> None`: Add an undirected edge between two nodes.

**Graph Traversal**:

- `dfs_recursive(start: int) -> List[int]`: Perform a recursive DFS starting from `start`.
- `dfs_iterative(start: int) -> List[int]`: Perform an iterative DFS starting from `start`.
- `bfs(start: int) -> List[int]`: Perform a BFS starting from `start`.

**Utility Methods**:

- `find_nodes_within_distance(start: int, n: int, method: str) -> Set[int]`: Find all nodes within `n` connections using either DFS or BFS.
- `find_shortest_path(start: int, end: int) -> Optional[List[int]]`: Find the shortest path between two nodes using BFS.

### Testing Requirements

Test your implementation using the `run_tests()` function from the starter file. The function will:
- Generate test graphs of varying sizes (small, medium, large).
- Test your DFS and BFS implementations for correctness and performance.
- Measure execution time and memory usage of your methods.
- Validate results for:
   - Nodes within a specified distance.
   - Shortest path calculations.

## Conclusion

This assignment challenges you to implement, analyze, and compare two fundamental graph traversal algorithms. Through this process, you'll gain practical experience in algorithm implementation and analysis, while developing the ability to make informed decisions about algorithm selection based on specific problem requirements.
