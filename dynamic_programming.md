# Dynamic Programming

## General Approach
- Look for two properties
    - Overlapping Subproblems - all DP problems will have this
    - Optimal Substructure
- Decide on the state
    - The smallest set of parameters that uniquely identify a certain position or standing in the problem.
- Formulate a relation among the states
    - How do you get to a state from the other states.
- Use Memoization or Tabulation
    - Memoization (Top Down) - Recursive solution that checks a lookup table before computing solution.
    - Tabulation (Bottom Up) - Builds a table from the bottom up and returns last entry in table.

## Fibonacci

### Top Down
```ruby
def fib_helper(n, cache)
  return cache[n] if cache[n]
  
  cache[n] = fib_helper(n - 1, cache) + fib_helper(n - 2, cache)
end


def fib(n)
  cache = { 1 => 1 , 2 => 1 }
  fib_helper(n, cache)
end
```

Or make a class:

```ruby
class Fib 
  def initialize 
    @cache = { 1 => 1, 2 => 1}
  end
  
  def fibs(n)
    return @cache[n] if @cache[n]
    
    ans = fibs(n - 1) + fibs(n - 2)
    @cache[n] = ans # save in cache before returning

    ans
  end
end
```

### Bottom Up
```ruby
def fib_cache_builder(n)
  cache = { 1 => 1 , 2 => 1 }
  return cache if n < 3
  
  (3..n).each do |i|
    cache[i] = cache[i - 1] + cache[i - 2]
  end
  
  cache 
end


def fib(n)
  cache = fib_cache_builder(n)
  cache[n]
end
```
