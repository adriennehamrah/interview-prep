# Graphs
- `|V|` = # vertices
- `|E|` = # edges
- directed - edges have direction - one way connection
- undirected - edges have no direction - two way connection
- if `|V| = n` 
  - `0 <= |E| <= n(n-1)`, if directed
  - `0 <= |E| <= n(n-1)/2`, if directed
- weighted graph - edges have an associated value
- density = |E| / |V| ( |V| - 1 )
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
### Edge list, Vertix List
    - store start vertex int, end vertex int, optional weight
    - vertex list: `O(|V|)` space
    - edge list: `O(|E|)` space
    - total space `O(|V| + |E|)`
    - finding adjecent nodes: `O(|E|)` time
    - find if given nodes are connected: `O(|E|)` time
### Adjacency Matrix
