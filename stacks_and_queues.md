# Stacks and Queues
## Stacks

### Max Min Stack
- Store the max and min values of the stack when you push a new element into the stack
- Peeking at the top element gives you the current max/min

### RPM Calculator
``` ruby
def eval_RPN(a)
  stack = []

  a.each do |el|
    if !stack.empty? && %w[+ - * /].include?(el)
      second = stack.pop.to_i
      first = stack.pop.to_i
      # send evaluates first arg (symbol or string), passing it the other args
      res = first.send(el, second) 
      stack << res
    else
      stack << el
    end
  end
  
  stack.first
end
```

## Queues
### Sliding Window Maximum
- Use a queue and always store index of max number as first element in queue
- `O(n)` time
```ruby
def sliding_maximum(a, b)
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
