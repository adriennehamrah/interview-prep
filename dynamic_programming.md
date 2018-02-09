## Fibonacci

### Top Down
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
