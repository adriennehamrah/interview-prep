# General Techniques and Concepts

## Binary Number
```ruby
 def findDigitsInBinary(a)
   return "0" if a == 0

   num = []
   while a > 0 
     num.unshift(a % 2)
     a /= 2
   end
   num.join
 end
```
or

```ruby
 def findDigitsInBinary(a)
   a.to_s(2)
 end
```

## Base Number Conversion
- For any base N, divide the decimal number by N and keep track of the remainders.

## Base 26 Conversion - number to alpha
- Subtract 1 to account for zero index array!
- Append to beginning so it's reversed

``` ruby
def numberToAlpha(a)
  alpha = ("A".."Z").to_a
  res = ""

  while a > 0 
    remainder = (a - 1) % 26
    result = alpha[remainder] + result
    a = (a - 1)/26
  end
  res
end
```

## Base 26 Conversion - alpha to number
- Reverse the string
- Keep track of index - this is like the 10th, 100th place
``` ruby
def alphaToNumber(a)
  alpha = ('A'..'Z').to_a
  res = 0
  a.reverse.split('').each_with_index do |ch, idx|
    pos = alpha.index(ch) + 1
    power = 26**idx
    res += power*pos
  end
  res
end
```
## Duplicate in Array
- Use a `Set` to keep track of seen values - O(n) space and traverse in O(1) time 

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

## Primes
- Check for prime factors up to the square root of `n`. Time complexity: `O(sqrt(n))`
- Remember to check for n = 0, 1 first

## Trailing Zeros
- Find number of multiples of 5, since 5*2 = 10, and there are far more 2's than 5's.
  - If dividing by 5 results in a decimal, truncate to whole number.
- Time Complexity: `O(logn)`

```ruby
 def trailingZeroes(a)
   i = 5
   count = 0
   while i <= a #i < 1
     count += a/i
     i *= 5
   end
   count
end
```
or

```ruby
def trailingZeroes(a)
  n = 0
  while(a != 0)
    n += a/5
    a/=5
  end
  n
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
