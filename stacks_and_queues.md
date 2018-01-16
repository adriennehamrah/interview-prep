# Stacks and Queues
## Stacks

## Queues
### Sliding Window Maximum
- Use a queue and always store index of max number as first element in queue
- `O(n)` time
```ruby
def slidingMaximum(a, b)
  res, queue = [], []

  (0..a.size-1).each do |i|
    queue.shift if !queue.empty? && i - queue.first >= b
    
    while !queue.empty? && a[i] >= a[queue.last]
      queue.pop
    end
    
    queue << i
    res << a[queue.first] if i >= b-1
  end
  
  res
end
```
