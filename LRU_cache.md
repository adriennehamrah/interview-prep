# LRU Cache
- Use hash map and linked list
- Remove the least recently used item in a cache (linked list) when it's full
- Hash map points to node object in linked list, allowing for O(1) lookup
- Delete, insert, and lookup are all O(1)

## Simplified LRU Cache in Ruby Using Built in Hash

``` ruby
class Node
  attr_accessor :key, :val, :next, :prev
  
  def initialize(key = nil, val = nil)
    @key = key
    @val = val
    @next = nil
    @prev = nil
  end
  
  def remove 
    if self.next
      self.next.prev = self.prev
    end
    
    if self.prev
      self.prev.next = self.next 
    end
    
    self.next = nil
    self.prev = nil 
    
    self
  end
end

class LRU
  def initialize(max)
    @hash = Hash.new
    @max = max
    @num_items = 0
    @head = Node.new
    @tail = Node.new
    @head.next = @tail
    @tail.prev = @head
  end
  
  def set(key, val)
    @num_items += 1
    if @num_items > @max
      first_node = @head.next
      @hash.delete(first_node.key)
      first_node.remove
      @num_items -= 1
   
    end
    
    append(key, val)
  end
  
  def get(key)
    node = @hash[key]
    if node
      node.remove
      @hash[key] = append(key, @hash[key].val)
      
      return node.val
    else
      return nil
    end
  end
  
  def append(key, val)
    node = Node.new(key, val)
    
    prev_node = @tail.prev
    prev_node.next = node
    node.prev = prev_node
    node.next = @tail 
    @tail.prev = node
    
    @hash[key] = node
    
    node
  end
end
```
