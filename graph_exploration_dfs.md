# Graph Exploration DFS

## Introduction

When working with graphs, Depth-First Search (DFS) is an important algorithm for exploring all vertices and edges. In this notebook, we'll implement DFS using NumPy and NetworkX to find a path between nodes in an unweighted, undirected graph.

## How Does DFS Work?

DFS explores a graph by going as deep as possible along each branch before backtracking:
1. We start at the source node and mark it as visited
2. We explore one of its neighbors completely (including all of that neighbor's neighbors) before moving to the next neighbor
3. When we can't go deeper, we backtrack to the last node with unexplored neighbors
4. This process continues until we reach the target node or visit all reachable nodes

Unlike BFS, DFS may not find the shortest path in unweighted graphs, but it is often more memory-efficient and well-suited for certain problems like cycle detection and topological sorting.

## Implementation with NumPy

Remember, it is forbidden to use any built-in functions or libraries that implement DFS. You need to implement the algorithm from scratch using NumPy and standard Python lists. Queues or stacks are not necessary for this implementation, as we can use NumPy arrays to store the visited nodes and track the exploration process. Any implementation that uses built-in DFS functions or Queue or Stack data structures will be considered invalid.

```python
def dfs_numpy(graph, source, target):
    """
    Implementation of DFS using NumPy and standard Python lists
    
    Parameters:
    - graph: NetworkX graph (undirected, unweighted)
    - source: Source node
    - target: Target node
    
    Returns:
    - steps: Number of steps needed to find the solution
    - path: List of nodes in the path from source to target
    """
    
    return steps, path
```

## Visual Example

Let's create a simple undirected graph to visualize how the algorithm works:

```python
def create_example_graph():
    """Creates an example undirected graph for testing"""
    G = nx.Graph()
    
    # Add nodes (cities)
    cities = ['Madrid', 'Barcelona', 'Valencia', 'Sevilla', 'Bilbao', 'Zaragoza']
    G.add_nodes_from(cities)
    
    # Add edges (no weights)
    edges = [
        ('Madrid', 'Barcelona'),
        ('Madrid', 'Valencia'),
        ('Madrid', 'Sevilla'),
        ('Madrid', 'Bilbao'),
        ('Madrid', 'Zaragoza'),
        ('Barcelona', 'Valencia'),
        ('Barcelona', 'Zaragoza'),
        ('Valencia', 'Sevilla'),
        ('Zaragoza', 'Bilbao')
    ]
    
    # Add the edges
    G.add_edges_from(edges)
    
    return G

# Create and visualize the graph
G = create_example_graph()

# Visualize the graph
pos = nx.spring_layout(G, seed=42)  # Node positioning
plt.figure(figsize=(10, 8))
nx.draw(G, pos, with_labels=True, node_color='lightblue', node_size=500, font_size=10)
plt.title("Undirected Graph of Spanish cities")
plt.show()
```

## Testing Our DFS Algorithm

Let's run our algorithm on this graph and see the results:

```python
# Define source and target nodes
source = 'Bilbao'
target = 'Sevilla'

# Run DFS
dfs_steps, dfs_path = dfs_numpy(G, source, target)
print(f"DFS Path from {source} to {target}:")
print(f"Number of steps: {dfs_steps}")
print(f"Path found: {dfs_path}")
print(f"Path length: {len(dfs_path) - 1} edges")

# Compare with NetworkX (shortest path)
shortest_path = nx.shortest_path(G, source, target)
print(f"\nNetworkX result (shortest path):")
print(f"Shortest path: {shortest_path}")
print(f"Path length: {len(shortest_path) - 1} edges")

# Check if DFS found the shortest path
if len(dfs_path) == len(shortest_path):
    print("\nDFS found the shortest path in this case!")
else:
    print(f"\nDFS found a valid path, but not the shortest one. Difference: {len(dfs_path) - len(shortest_path)} edges")
```

## Visualizing the DFS Process

Let's visualize the path that DFS finds:

```python
def visualize_path(G, path, title):
    """Visualizes the path with numbered edges using edge labels"""
    plt.figure(figsize=(10, 8))
    
    # Create a copy of the graph for visualization
    H = G.copy()
    pos = nx.spring_layout(H, seed=42)
    
    # Create the edges of the path
    edge_colors = []
    edge_widths = []
    
    # Create edge labels dictionary for the path edges
    edge_labels = {}
    
    # Process all edges and mark the path edges
    for u, v in H.edges():
        if len(path) > 1:
            # Check if this edge is part of the path
            is_path_edge = False
            for i in range(len(path) - 1):
                if (u == path[i] and v == path[i+1]) or \
                   (v == path[i] and u == path[i+1]):  # For undirected graphs
                    is_path_edge = True
                    # Add label with the step number
                    edge_labels[(u, v)] = str(i + 1)
                    break
            
            if is_path_edge:
                edge_colors.append('red')
                edge_widths.append(3.0)
            else:
                edge_colors.append('gray')
                edge_widths.append(1.0)
        else:
            edge_colors.append('gray')
            edge_widths.append(1.0)
    
    # Draw all nodes
    nx.draw_networkx_nodes(H, pos, node_color='lightblue', node_size=500)
    
    # Highlight the nodes in the path
    nx.draw_networkx_nodes(H, pos, nodelist=path, node_color='#ff9999', node_size=500)
    
    # Draw all edges with appropriate colors and widths
    nx.draw_networkx_edges(H, pos, edge_color=edge_colors, width=edge_widths, alpha=0.7)
    
    # Draw edge labels (numbers) for the path
    nx.draw_networkx_edge_labels(H, pos, edge_labels=edge_labels, font_size=12, 
                                font_weight='bold', bbox=dict(facecolor='white', alpha=0.7))
    
    # Draw node labels
    nx.draw_networkx_labels(H, pos)
    
    plt.title(title)
    plt.axis('off')
    plt.show()

# Visualize the DFS path with numbered edges
visualize_path(G, dfs_path, "DFS Path with Numbered Edges")

# Also visualize the shortest path for comparison
visualize_path(G, shortest_path, "Shortest Path with Numbered Edges (for comparison)")
```

## Comparing DFS and BFS

Let's highlight the key differences between DFS and BFS for graph traversal:

```python
# Run both algorithms on the same source-target pair
source = 'Bilbao'
target = 'Sevilla'

# For this example, we'll assume we have both DFS and BFS implementations
dfs_steps, dfs_path = dfs_numpy(G, source, target)
# Let's assume we also have the BFS result (using the previously implemented BFS algorithm)
bfs_steps, bfs_path = bfs_numpy(G, source, target)

print(f"Comparison of DFS and BFS from {source} to {target}:")
print(f"DFS steps: {dfs_steps}, path length: {len(dfs_path) - 1}")
print(f"BFS steps: {bfs_steps}, path length: {len(bfs_path) - 1}")

print("\nDFS Path:")
print(" -> ".join(dfs_path))

print("\nBFS Path (Shortest Path):")
print(" -> ".join(bfs_path))
```

## Conclusion

In this notebook, we have explored the Depth-First Search algorithm implemented using NumPy and NetworkX. DFS is a fundamental graph traversal method that explores as far as possible along each branch before backtracking. Unlike BFS, DFS may not find the shortest path in unweighted graphs, but it has several advantages for certain applications:

1. DFS generally requires less memory than BFS, as it doesn't need to store all nodes at a given depth level
2. DFS is well-suited for problems like topological sorting, finding connected components, and cycle detection
3. DFS can be implemented recursively (although we used an iterative approach here)

Our implementation leverages NumPy's efficient array operations and NetworkX's graph representation capabilities, demonstrating how these tools can be combined to solve graph-related problems effectively. The visualization of the path provides an intuitive understanding of how DFS works and how it differs from BFS. This algorithm is essential in many applications, including maze generation and solving, web crawling with specific depth limits, and searching in game trees.

## Exercise

### Exercise 1

After we implemented the DFS algorithm using NumPy, now it's time to understand the algorithm. What we want you to do is to explain the algorithm in your own words, and try to execute each step of the algorithm, showing print statements for each step. This will help you understand the algorithm better and see how it works in practice.

### Exercise 2

Apply the DFS algorithm to the synthetic graphs that you generated in the previous notebook, and discuss the results. How does the algorithm perform on these graphs? How does the DFS path compare to the shortest path found by BFS? In what cases might DFS be more appropriate than BFS?