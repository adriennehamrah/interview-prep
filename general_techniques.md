# General Techniques and Concepts

## Linked List 
- Head and tail can either have value of `nil` or be sentinal nodes (dummy nodes that do not hold a value)
- Sentinal nodes avoids type checking for nil

## Hash Map
- Key value pairs stored in hash buckets of Linked Lists
- Hash the key before moding by number of buckets
- Resize when number of items in linked list is >= total number of buckets
- Delete, insert, and lookup are all O(1)

## LRU Cache
- Use hash map and linked list
- Remove the least recently used item in a cache (linked list) when it's full
- Hash map points to node object in linked list, allowing for O(1) lookup
- Delete, insert, and lookup are all O(1)

## Primes
- Check for prime factors up to the square root of `n`. Time complexity: `O(sqrt(n))`
- Remember to check for n = 0, 1, or 2 first.

## Graphs
- |V| = # vertices
- |E| = # edges
- density = |E| / |V| ( |V| - 1 )
  - max density = 1 (undirected), 2 (directed)
  - min density = 0

## Topological Sort
### Use Cases
- Scheduling tasks/dependencies
- Webpack
- Minimal Spanning Tree
### Kahn's Alogorithm
1. Queue all vertices with no in-edges
2. Pop off vertices from queues
 - Remove vertex and out-edges
 - Push vertex into sorted array
 - Examine destination vertices. Push and queue if no more in-edges
 - Repeat
 ### Coffman-Graham Algorithm
 - Modified Kahn's that is deterministic
 ### Depth First Search
