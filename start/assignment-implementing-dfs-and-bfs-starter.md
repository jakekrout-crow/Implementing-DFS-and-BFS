```python

# Starter Code
# Performance Analyzer Class
class PerformanceAnalyzer:
    @staticmethod
    def measure_execution_time(func, *args) -> Tuple[float, any]:
        """Measure execution time of a function."""
        start_time = time.perf_counter()
        result = func(*args)
        end_time = time.perf_counter()
        return end_time - start_time, result

    @staticmethod
    def measure_memory_usage(func, *args) -> Tuple[float, any]:
        """Measure memory usage of a function."""
        tracemalloc.start()
        result = func(*args)
        current, peak = tracemalloc.get_traced_memory()
        tracemalloc.stop()
        return peak / 10**6, result  # Convert to MB

# Test Runner
def run_tests():
    def generate_test_graph(num_nodes: int, density: float) -> Graph:
        g = Graph()
        for i in range(num_nodes):
            g.add_node(i)
        max_edges = (num_nodes * (num_nodes - 1)) // 2
        num_edges = int(max_edges * density)
        edges_added = 0
        while edges_added < num_edges:
            node1 = random.randint(0, num_nodes - 1)
            node2 = random.randint(0, num_nodes - 1)
            if node1 != node2 and node2 not in g.graph[node1]:
                g.add_edge(node1, node2)
                edges_added += 1
        print(f"Generated graph with {num_nodes} nodes and {edges_added} edges.")
        return g

    test_cases = [
        (20, 0.3, "small network (20 nodes)"),
        (200, 0.1, "medium network (200 nodes)"),
        (1000, 0.05, "large network (1000 nodes)"),
    ]

    for num_nodes, density, description in test_cases:
        print(f"Testing {description}...")
        graph = generate_test_graph(num_nodes, density)
        analyzer = PerformanceAnalyzer()

        time_dfs, dfs_result = analyzer.measure_execution_time(graph.dfs_recursive, 0)
        time_bfs, bfs_result = analyzer.measure_execution_time(graph.bfs, 0)
        print(f"DFS execution time: {time_dfs:.10f} seconds")
        print(f"BFS execution time: {time_bfs:.10f} seconds")

        distance = 2
        time_dfs_dist, dfs_dist_result = analyzer.measure_execution_time(
            graph.find_nodes_within_distance, 0, distance, 'dfs')
        time_bfs_dist, bfs_dist_result = analyzer.measure_execution_time(
            graph.find_nodes_within_distance, 0, distance, 'bfs')
        print(f"Finding nodes within distance {distance}:")
        print(f"DFS time: {time_dfs_dist:.10f} seconds")
        print(f"BFS time: {time_bfs_dist:.10f} seconds")

        time_path, path_result = analyzer.measure_execution_time(graph.find_shortest_path, 0, 5)
        print(f"Shortest path finding time: {time_path:.10f} seconds")
        print(f"Path found: {path_result}")
        print()

# Run Tests
run_tests()

```