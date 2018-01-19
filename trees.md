# Trees

# Max Depth
```ruby
def max_depth(a)
  return 0 if a.nil?

  1 + [max_depth(a.left), max_depth(a.right)].max
end
```

# Min Depth
- Level order traversal and return first leaf node
- Keep track of depth
```ruby
def min_depth(root)
  return 0 unless root
       
  q = []
  q  << { node: root, depth: 1 }

  while !q.empty?
    queueItem = q.shift
    node = queueItem[:node]
    depth = queueItem[:depth]

    if node.left.nil? && node.right.nil?    
        return depth 
    end 
    
    q << { node: node.left, depth: depth + 1 } if node.left
    q << { node: node.right, depth: depth + 1 } if node.right
  end

end
```

## In Order Traversal (left, root, right)
```ruby
def in_order_traversal(root)
  stack = []
  res = []
  curr = root
  
  while !stack.empty? || curr
    if curr
      stack << curr
      curr = curr.left
    else
      curr = stack.pop
      res << curr.data
      curr = curr.right
    end
  end
  
  res
end
```

## Pre-Order Traversal (root, left, right)
```ruby
def preorder_traversal(root)
  stack = []
  res = []
  curr = root
  
  while !stack.empty? || curr
    if curr
      stack << curr 
      res = curr.data
      curr = curr.left 
    else
      curr = stack.pop 
      curr = curr.right
  end
  
  res
end
```

## Post-Order Travesal (left, right, root)
- Reverse
``` ruby
def postorder_traversal(root)
  return [] unless root
  
  node = root
  stack = [node]
  res = []
  
  while !stack.empty?
    node = stack.pop
    res << node.data
    stack << node.left if node.left
    stack << node.right if node.right
  end
  
  res.reverse
end
```

- Unshift
```ruby
def postorder_traversal(root)
  stack = []
  res = []
  curr = root
  
  while !stack.empty? || curr
    if curr
      stack << curr
      res.unshift(curr.data)
      curr = curr.right
    else
      curr = stack.pop
      curr = curr.left
    end
  end
  
  res
end
```

## Vertical Order Traversal
- Print out nodes from left to right
- If two nodes share the same vertical line, the lesser depth node comes first
- Use breadth first approach and save horizontal distance of each node
- Put nodes in hash, with horizontal distance as key
- Sort hash by horizontal distance, smallest to largest

``` ruby
def vert_order_util(root, horizontal_distance)
  return [] unless root 
  
  res = Hash.new { |k,v| k[v] = [] }
  curr = [root, 0]
  queue = [curr]
  
  while !queue.empty?
    curr = queue.shift
    node = curr.first
    hd = curr.last
    
    res[curr.last] << node.data 
    
    queue << [node.left, hd - 1 ] if node.left
    queue << [node.right, hd + 1 ] if node.right
  end
  
  res.sort_by{ |k,v| k }.map(&:last)
end

def vertical_order_traversal(root)
  vert_order_util(root, 0)
end
```

## Zig Zag Traversal
- Use breadth first and reverse for each row
```
def zigzag_levelorder(root)
  return [] unless root
  
  queue = [root]
  ans = []
  mod = 0
  
  while !queue.empty?
    i = 0
    n = queue.length
    list = []
    
    while i < n
      node = queue.shift
      queue << node.left if node.left
      queue << node.right if node.right
      list << node.data
      i += 1
    end
    
    if mod % 2 == 0
      ans << list 
    else
      ans << list.reverse
    end
    
    mod += 1 
  end
  
  ans
end
```

## Valid BST?
- Solution 1: Use recursion and min/max `O(n) time` as opposed to no min/max `O(n^2)`
- Solution 2: In order traversal with a stack and check that previous values are always smaller `O(n)`
``` ruby
class Integer
    MAX = 2^32
    MIN = -MAX
end

def is_valid?(root, max, min)
    return 1 if root.nil?

    if (root.data <= min) || (root.data >= max)
        return 0
    end

    is_valid?(root.left, root.data, min) & is_valid?(root.right, max, root.data)
end

def is_valid_BST(root)
    is_valid?(root, Integer::MAX, Integer::MIN)
end
```

```ruby
def is_valid_BST(root)
  return 1 unless root
  stack = []
  prev = nil
  
  while(root || !stack.empty?)
    if(root)
      stack << root
      root = root.left
    else
      root = stack.pop
      return 0 if(prev && root.data <= prev.data)
      
      prev = root
      root = root.right
    end
  end
  
  return 1
end
```

## Next Immediate Successor BST (next greatest value)

``` python
# @param A : root node of tree
# @param B : integer

def get_successor(self, A, B):
    root = A
    succ = root

    while root.val != B:
        if B > root.val:
            root = root.right
        else:
            succ = root
            root = root.left
    if root.right != None:
        root = root.right
        while root.left!= None:
            root = root.left
        return root
    else:
        if succ.val <= B:
            return None
        else:
            return succ
```
