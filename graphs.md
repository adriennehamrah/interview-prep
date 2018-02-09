# Graphs
- `|V|` = # vertices
- `|E|` = # edges
- directed - edges have direction - one way connection
- undirected - edges have no direction - two way connection
- if `|V| = n` 
  - `0 <= |E| <= n(n-1)`, if directed
  - `0 <= |E| <= n(n-1)/2`, if directed
- weighted graph - edges have an associated value
- density of simple, directed graph = `|E| / |V| ( |V| - 1 )`
  - max density = 1 (undirected), 2 (directed)
  - min density = 0
  - dense graphs - adjacency matrix
  - sparse graphs - adjacency list
- self loop (website refers to itself)
- multi edge (multiple flight options to/from same airport)
- paths (walks)
   - simple path - no vertices, and thus edges, are repeated
   - trail - walk in which no edges are repeated
   - closed walk - starts and ends at same vertex, length > 0 
   - simple cycle - closed walk with no repetition other than start and end
- acyclic graph - has no cycles
    - tree
- directed acyclic graph (DAG)
- strongly connected - there is a path from any vertex to any other vertex

## Implementations
### Edge List
- Store start vertex int, end vertex int, optional weight
- Vertex list: `O(|V|)` space
- Edge list: `O(|E|)` space
- Total space: `O(|V| + |E|)`
- Finding adjecent nodes: `O(|E|)` time
- Find if given nodes are connected: `O(|E|)` time
### Adjacency Matrix
- Store edges in a matrix (2D array), with name and indices as key-val pairs in hash table
    - Unweighted - store 1 or 0 for val
    - Weighted - store weighted values and some val that will never be an edge weight
- Undirected matric is symmetric A[i][j] = A[j][i]. Only need to go through first diagonal half.
- Total space: `O(|V|^2)` - Very space heavy, not efficient for sparse graphs like most real world graphs!
- Finding adjecent nodes: `O(|V|)` time
- Find if given nodes are connected: `O(1)`
### Adjacency List
- Store edges in rows of linked lists of varying size, storing only existing edges. Have seperate array of pointers to head of LL
- Total space: `O(|E| + |V|)`
- Finding adjecent nodes: `O(|V|)` time
- Find if given nodes are connected: `O(|V|)` - linear search of rows, `O(log|V|)` - binary search
- Considered BST for improved addition and deletion

## Depth First Traversal
## Breadth First Traversal

## Topological Sort
- Linearing ordering of vertices such that for every directed edge uv, vertex u comes before v
- Only possible for a DAG (Directed Acyclic Graph)
- Can be more than one sorting

### Use Cases
- Scheduling tasks/dependencies
- Package install, NPM
- Module bundling, Webpack
- Minimal Spanning Tree

### Tarjan's Algorithm
- Based on a modified DFS
1. Visit vertices in random order.
2. Add current node to visited set.
3. Check all adjacent vertices of this node. If all adjacent vertices have been visited or the node is a leaf node, add this node to the stack.
4. Repeat with other unvisited vertices.
5. After visiting every vertex, print out stack.

### Kahn's Algorithm
1. Queue all vertices with no in-edges
2. Pop off vertices from queues
 - Remove vertex and out-edges
 - Push vertex into sorted array
 - Examine destination vertices. Push and queue if no more in-edges
 - Repeat
 ### Coffman-Graham Algorithm
 - Modified Kahn's that is deterministic

