# General Techniques and Concepts

## Factors
- Need to only check up to sqrt of `n`

```ruby
  def allFactors(n)
    factors = []
    limit = (n**0.5).to_i
    (1..limit).each do |num|
      if n % num == 0
        factors << num
        factors << n / num
      end
    end
    
    return factors.uniq.sort
    end
```

## GCD
- `gcd(m, n) = gcd(m % n, n)` for `m > n` 
- Find max of two numbers first, swap as necessary
- Check if `m` or `n` is zero first - every integer is a divisor of zero

```ruby
 def gcd(a, b)
   a, b = b, a if b > a
   if b == 0
     return a
   end
  
   return gcd( b, a % b)       
 end
```

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

## Heap Sort
### Binary Heap
- A complete binary tree where the parent node value is either always greater (max heap) or smaller (min heap)
- Array based representation
  - Children indices are `2i + 1`, `2i + 2`
- Peeking at min/max O(1)
- Insertion O(log n)
- Extraction O(log n)

### Implementation
- O(n log n) worse case
- Build a max heap of size n
- The root element will be the largest in the array 
  - Swap the root with the last element to remove to root
  - Heapify down to place the swapped element in the right position
  - Decrease the length by 1
- Repeat until size is 1

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
