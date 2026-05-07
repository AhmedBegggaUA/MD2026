# Graph Exploration Random Walks

## Introduction

When working with graphs, Random Walks provide an alternative exploration strategy that mimics random movement through a network. In this notebook, we'll implement Random Walks using NumPy and NetworkX to explore an unweighted, undirected graph and potentially find a path between nodes.

## How Do Random Walks Work?

Random Walks explore a graph by moving randomly from node to node:
1. We start at the source node and mark it as visited
2. At each step, we randomly select one of the current node's neighbors
3. We move to that neighbor and add it to our path
4. This process continues until we reach the target node or exceed a maximum number of steps

Unlike BFS and DFS, Random Walks don't guarantee finding the shortest path or even any path at all, but they are useful for sampling graph properties, simulating stochastic processes, and can be effective in very large graphs where systematic exploration is impractical.

## Implementation with NumPy

Remember, it is forbidden to use any built-in functions or libraries that implement Random Walks. You need to implement the algorithm from scratch using NumPy and standard Python lists. Any implementation that uses built-in Random Walk functions will be considered invalid.

```python
import numpy as np
import networkx as nx
import matplotlib.pyplot as plt

def random_walk_numpy(graph, source, target, max_steps=1000, seed=42):
    """
    Implementation of Random Walk using NumPy and standard Python lists
    
    Parameters:
    - graph: NetworkX graph (undirected, unweighted)
    - source: Source node
    - target: Target node
    - max_steps: Maximum number of steps before giving up
    - seed: Random seed for reproducibility
    
    Returns:
    - steps: Number of steps needed to find the solution
    - path: List of nodes in the path from source to target
    - success: Boolean indicating whether the target was found
    """
    
    return steps, node_path, success
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

## Testing Our Random Walk Algorithm

Let's run our algorithm on this graph and see the results:

```python
# Define source and target nodes
source = 'Bilbao'
target = 'Sevilla'

# Run Random Walk
rw_steps, rw_path, success = random_walk_numpy(G, source, target, max_steps=100, seed=42)

if success:
    print(f"Random Walk from {source} to {target}:")
    print(f"Number of steps: {rw_steps}")
    print(f"Path found: {rw_path}")
    print(f"Path length: {len(rw_path) - 1} edges")
else:
    print(f"Random Walk failed to find {target} from {source} within {rw_steps} steps.")
    print(f"Partial path: {rw_path}")

# Compare with NetworkX (shortest path)
shortest_path = nx.shortest_path(G, source, target)
print(f"\nNetworkX result (shortest path):")
print(f"Shortest path: {shortest_path}")
print(f"Path length: {len(shortest_path) - 1} edges")

# Check if Random Walk found the shortest path (unlikely)
if success and len(rw_path) == len(shortest_path):
    print("\nRandom Walk found the shortest path by chance!")
elif success:
    print(f"\nRandom Walk found a valid path, but not the shortest one. Difference: {len(rw_path) - len(shortest_path)} edges")
```

## Visualizing the Random Walk Process

Let's visualize the path that the Random Walk finds:

```python
def visualize_random_walk_path(G, path, title):
    """Visualizes the random walk path with arrows indicating direction"""
    plt.figure(figsize=(10, 8))
    
    # Create a copy of the graph for visualization
    H = G.copy()
    pos = nx.spring_layout(H, seed=42)
    
    # Create directed edges for the path to show the walk direction
    path_edges = [(path[i], path[i+1]) for i in range(len(path)-1)]
    
    # Draw all nodes
    nx.draw_networkx_nodes(H, pos, node_color='lightblue', node_size=500)
    
    # Highlight the nodes in the path
    nx.draw_networkx_nodes(H, pos, nodelist=path, node_color='#ff9999', node_size=500)
    
    # Draw all edges in gray
    nx.draw_networkx_edges(H, pos, edge_color='gray', width=1.0, alpha=0.5)
    
    # Draw the random walk path with arrows
    nx.draw_networkx_edges(
        H, pos, 
        edgelist=path_edges, 
        edge_color='red', 
        width=2.0, 
        arrows=True,  # Show arrows for direction
        arrowstyle='-|>',  # Arrow style
        arrowsize=15,
        connectionstyle='arc3,rad=0.1'  # Curved edges to show direction better
    )
    
    # Add numbers to show the order of steps
    edge_labels = {path_edges[i]: str(i+1) for i in range(len(path_edges))}
    nx.draw_networkx_edge_labels(
        H, pos, 
        edge_labels=edge_labels, 
        font_size=10,
        font_weight='bold', 
        bbox=dict(facecolor='white', alpha=0.7)
    )
    
    # Draw node labels
    nx.draw_networkx_labels(H, pos)
    
    plt.title(title)
    plt.axis('off')
    plt.show()

# Visualize the Random Walk path with arrows
if success:
    visualize_random_walk_path(G, rw_path, "Random Walk Path with Step Numbers")
```
## Practical Applications of Random Walks

Random Walks have many practical applications in various fields:

1. **PageRank Algorithm**: Google's original algorithm uses random walks to rank web pages based on the probability of a random surfer visiting them.

2. **Recommendation Systems**: Random walks on user-item graphs can be used to generate personalized recommendations.

3. **Network Sampling**: Random walks provide a way to sample nodes from large networks when complete exploration is impractical.

4. **Community Detection**: Random walk-based metrics can identify densely connected communities in networks.


## Conclusion

In this notebook, we have explored the Random Walk algorithm implemented using NumPy and NetworkX. Random Walks provide a stochastic approach to graph traversal that differs fundamentally from deterministic methods like BFS and DFS. While random walks do not guarantee finding the shortest path or even any path at all, they have several advantages:

1. They require minimal memory as they only need to track the current position and path
2. They can be effective for exploring very large graphs where systematic traversal is impractical
3. They model many natural and social processes that involve random movement
4. They form the basis for many important algorithms in recommendation systems, web ranking, and network analysis

Our implementation demonstrates how random walks behave in graphs and highlights the trade-off between deterministic exploration and stochastic sampling. The visualization of the walk paths provides an intuitive understanding of how randomness affects exploration patterns. This algorithm is essential in many applications, including PageRank, recommendation systems, and Markov Chain Monte Carlo methods.

## Exercise

### Exercise 1

After implementing the Random Walk algorithm using NumPy, now it's time to understand the algorithm. What we want you to do is to explain the algorithm in your own words, and try to execute each step of the algorithm, showing print statements for each step. This will help you understand the algorithm better and see how it works in practice.

### Exercise 2

Apply the Random Walk algorithm to the synthetic graphs that you generated in the previous notebook, and discuss the results. How does the algorithm perform on these graphs? In what cases might Random Walks be more appropriate than BFS or DFS? Pay attention to the differences in path lengths and the nature of the paths found by each algorithm.

## Submission

For the delivery of the practice 3, what you will be asked to do is to make a zip (name_name.zip) containing 4 notebooks: a first notebook containing the generation section, a second notebook containing BFS, a third notebook containing the DFS algorithm and a fourth notebook containing the Random Walk algorithm.

At the end the zip should be like this when you unzip it:
```bash
name_surname.zip
├── graph_exploration_bfs.ipynb
├── graph_exploration_dfs.ipynb
├── graph_exploration_rw.ipynb
└── graph_exploration_generation.ipynb

```