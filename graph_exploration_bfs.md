# Graph Exploration BFS

## Introduction

When working with unweighted graphs, Breadth-First Search (BFS) is the optimal algorithm for finding the shortest path between nodes. In this notebook, we'll implement BFS using NumPy and NetworkX to find the shortest path in an unweighted, undirected graph.


## How Does BFS Work?

BFS explores a graph level by level, starting from a source node:
1. We start at the source node and mark it as visited
2. We explore all its immediate neighbors
3. Then we move to the next level of nodes (neighbors of neighbors)
4. This process continues until we reach the target node or visit all reachable nodes

Since BFS explores nodes in order of their distance from the source, it naturally finds the shortest path in unweighted graphs.

## Implementation with NumPy

Remember, it is forbidden to use any built-in functions or libraries that implement BFS. You need to implement the algorithm from scratch using NumPy and standard Python lists. Queues or stacks are not necessary for this implementation, as we can use NumPy arrays to store the visited nodes and track the exploration process. Any implementation that uses built-in BFS functions or Queue or Stack data structures will be considered invalid.

```python


def bfs_numpy(graph, source, target):
    """
    Implementation of BFS using NumPy and standard Python lists
    
    Parameters:
    - graph: NetworkX graph (undirected, unweighted)
    - source: Source node
    - target: Target node
    
    Returns:
    - steps: Number of steps needed to find the solution
    - shortest_path: List of nodes in the shortest path from source to target
    """
    
    
    return steps, shortest_path
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

## Testing Our BFS Algorithm

Let's run our algorithm on this graph and see the results:

```python
# Define source and target nodes
source = 'Bilbao'
target = 'Sevilla'

# Run BFS
bfs_steps, bfs_visited = bfs_numpy(G, source, target)
print(f"BFS Path from {source} to {target}:")
print(f"Number of steps: {bfs_steps}")
print(f"Visited nodes: {bfs_visited}")
print(f"Number of nodes visited: {len(bfs_visited)}")

# Compare with NetworkX
path = nx.shortest_path(G, source, target)
print(f"\nNetworkX result:")
print(f"Shortest path: {path}")
print(f"Path length: {len(path) - 1} edges")
```

## Visualizing the BFS Process

Let's visualize the order in which BFS visits the nodes:

```python
def visualize_shortest_path(G, shortest_path, title):
    """Visualizes the shortest path with numbered edges using edge labels"""
    plt.figure(figsize=(10, 8))
    
    # Create a copy of the graph for visualization
    H = G.copy()
    pos = nx.spring_layout(H, seed=42)
    
    # Create the edges of the shortest path
    edge_colors = []
    edge_widths = []
    
    # Create edge labels dictionary for the shortest path edges
    edge_labels = {}
    
    # Process all edges and mark the shortest path edges
    for u, v in H.edges():
        if len(shortest_path) > 1:
            # Check if this edge is part of the shortest path
            is_path_edge = False
            for i in range(len(shortest_path) - 1):
                if (u == shortest_path[i] and v == shortest_path[i+1]) or \
                   (v == shortest_path[i] and u == shortest_path[i+1]):  # For undirected graphs
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
    
    # Highlight the nodes in the shortest path
    nx.draw_networkx_nodes(H, pos, nodelist=shortest_path, node_color='#ff9999', node_size=500)
    
    # Draw all edges with appropriate colors and widths
    nx.draw_networkx_edges(H, pos, edge_color=edge_colors, width=edge_widths, alpha=0.7)
    
    # Draw edge labels (numbers) for the shortest path
    nx.draw_networkx_edge_labels(H, pos, edge_labels=edge_labels, font_size=12, 
                                font_weight='bold', bbox=dict(facecolor='white', alpha=0.7))
    
    # Draw node labels
    nx.draw_networkx_labels(H, pos)
    
    plt.title(title)
    plt.axis('off')
    plt.show()

# Visualize the shortest path with numbered edges
visualize_shortest_path(G, path, "Shortest Path with Numbered Edges")
```

## Conclusion

In this notebook, we have explored the Breadth-First Search algorithm implemented using NumPy and NetworkX. BFS is a fundamental graph traversal method that systematically explores all vertices of a graph by visiting neighbors at each level before moving to the next level. This level-by-level approach naturally leads to finding the shortest path in unweighted graphs, making BFS an optimal choice for such scenarios. Our implementation leverages NumPy's efficient array operations and NetworkX's graph representation capabilities, demonstrating how these tools can be combined to solve graph-related problems effectively. The visualization of the visit order provides an intuitive understanding of how BFS works and why it guarantees the shortest path in unweighted graphs. This algorithm forms the foundation for many more complex graph algorithms and is essential in network analysis, web crawling, social network analysis, and many other applications where finding the most direct connection between nodes is crucial.


## Exercise

### Exercise 1

After we implemented the BFS algorithm using NumPy, now it's time to understand the algorithm. What we want you to do is to explain the algorithm in your own words, and try to execute each step of the algorithm, showing print statements for each step. This will help you understand the algorithm better and see how it works in practice.

### Exercise 2

Apply the BFS algorithm to the synthetic graphs that you generated in the previous notebook, and discuss the results. How does the algorithm perform on these graphs? Why it takes more steps to find the shortest path in some cases?