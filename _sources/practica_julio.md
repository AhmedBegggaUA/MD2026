# Recovery Practice

**Maximum time:** 1 week  
**Submission deadline:** 10/07/2025

## Introduction

This recovery practice integrates all concepts covered in the four previous practices. You will work with a social network dataset to apply graph analysis, visualization, and exploration techniques that you have learned throughout the course.

## Dataset: Zachary's Karate Club Social Network

You will use the famous "Zachary's Karate Club" dataset, which represents social relationships between members of a university karate club. This dataset is ideal because:
- It's a real graph with clear community structure
- It has a manageable size (34 nodes, 78 edges)
- It's available in NetworkX
- It allows applying all course concepts

```python
import networkx as nx
# Load the dataset
G = nx.karate_club_graph()
```

---

## Exercise 1: NumPy Analysis (25%)

### Section 1.1: Fundamental matrices (15%)
Using **only NumPy** and basic NetworkX functions (without using predefined functions for matrix calculations), implement and calculate:

1. **Adjacency matrix** of the graph
2. **Degree matrix** (diagonal matrix with the degrees of each node)
3. **Laplacian matrix** (D - A)
4. **Normalized Laplacian matrix** (D^(-1/2) * L * D^(-1/2))

```python
def calculate_matrices(G):
    """
    Calculates fundamental matrices of the graph using NumPy
    
    Returns:
    - adjacency_matrix: adjacency matrix
    - degree_matrix: degree matrix
    - laplacian_matrix: laplacian matrix
    - normalized_laplacian: normalized laplacian matrix
    """
    # Your implementation here
    return adjacency_matrix, degree_matrix, laplacian_matrix, normalized_laplacian
```

### Section 1.2: Connectivity analysis (10%)
Implement a function that finds all nodes with degree greater than or equal to a given value:

```python
def find_high_degree_nodes(adjacency_matrix, min_degree):
    """
    Finds nodes with degree >= min_degree
    
    Parameters:
    - adjacency_matrix: adjacency matrix
    - min_degree: minimum degree
    
    Returns:
    - numpy array with indices of nodes that meet the condition
    - if no nodes exist, return array with [-1]
    """
    # Your implementation here
    return high_degree_nodes
```

**Deliverables:** Notebook `numpy_analysis.ipynb` with all calculations, printed matrices, and result analysis.

---

## Exercise 2: Visualization and Analysis with Pandas/Matplotlib/NetworkX (25%)

### Section 2.1: DataFrame creation (10%)
Create a Pandas DataFrame containing information for each node:

```python
# Required DataFrame structure:
# - node_id: node identifier
# - degree: node degree  
# - clustering: clustering coefficient
# - betweenness: betweenness centrality
# - closeness: closeness centrality
# - community: community to which it belongs (use nx.community.greedy_modularity_communities)
# - connections: list of neighboring nodes
```

### Section 2.2: Visualizations (15%)
Create **4 different visualizations** using Matplotlib and/or Seaborn:

1. **Degree distribution histogram**
2. **Scatter plot** of betweenness centrality vs closeness
3. **Bar chart** showing average degree per community
4. **Graph visualization** with nodes colored by community and size proportional to degree

Each visualization must have:
- Descriptive title
- Axis labels
- Legend when appropriate
- Comments explaining what it shows

**Deliverables:** Notebook `visualization_analysis.ipynb`, DataFrame exported as `karate_network_data.csv`, and the 4 visualizations saved as PNG files.

---

## Exercise 3: Graph Exploration (25%)

### Section 3.1: Algorithm implementation (15%)
Implement **from scratch** (using only NumPy and Python lists) the three exploration algorithms, and the most important, **DO A TRACE OF THE STEPS** as we did during the practice:
```{Note}
In class, we implemented these algorithms, so you can use those implementations, but It is compulsory to implement a trace of the algorithms. Otherwise, you will get a 0 in this exercise.
```
```python
def bfs_implementation(graph, source, target):
    """
    BFS implemented from scratch
    Returns: (steps, path)
    """
    # Your implementation here
    return steps, path

def dfs_implementation(graph, source, target):
    """
    DFS implemented from scratch  
    Returns: (steps, path)
    """
    # Your implementation here
    return steps, path

def random_walk_implementation(graph, source, target, max_steps=1000, seed=42):
    """
    Random Walk implemented from scratch
    Returns: (steps, path, success)
    """
    # Your implementation here
    return steps, path, success
```

### Section 3.2: Comparative analysis (10%)
Execute the three algorithms to find paths between **5 different pairs** of nodes (you choose the pairs). For each pair:

1. Execute each algorithm
2. Compare length of found paths
3. Analyze number of steps needed

Create a summary table with results and discuss observed differences.

**Deliverables:** Notebook `graph_exploration.ipynb` with implementations, tests, and comparative analysis.

---

## Exercise 4: Node2Vec and Classification (25%)

### Section 4.1: Node2Vec implementation and application (25%)
Using the Node2Vec code provided in classes:

1. **Apply Node2Vec** to the karate club graph
2. **Experiment with different parameters:**
   - Embedding dimensions: [8, 16, 32]
   - Number of walks: [10, 20, 50]
   - Walk length: [10, 20, 40]
3. **Visualize embeddings** using PCA to reduce to 2D
4. **Color points** according to the real community of each node

**Deliverables:** Notebook `node2vec_analysis.ipynb`.

---

## Submission

### Final ZIP structure:
```
lastname_firstname.zip
├── numpy_analysis.ipynb
├── visualization_analysis.ipynb  
├── graph_exploration.ipynb
├── node2vec_analysis.ipynb
├── visualization1.png
├── visualization2.png
├── visualization3.png
└── visualization4.png
```

### Evaluation criteria:

- **Code correctness:** 40%
- **Analysis and discussion:** 30%
- **Visualization quality:** 20%
- **Structure and documentation:** 10%

### Important notes:

1. **You CANNOT use predefined functions** for algorithms you must implement from scratch
2. **Document your code well** with explanatory comments
3. **Include analysis and conclusions** in each exercise
4. **Use appropriate seeds** for reproducibility
5. **Follow best practices** seen in class

**Good luck with your recovery practice!**