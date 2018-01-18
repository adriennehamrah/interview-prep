# Trees
## In Order Traversal (left, root, right)
```ruby
def inorderTraversal(root)
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
def preordertraversal(root)
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
def postorderTraversal(root)
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
def postorderTraversal(root)
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

## Valid BST?
- Solution 1: Use recursion and min/max `O(n) time` as opposed to no min/max `O(n^2)`
- Solution 2: In order traversal with a stack and check that previous values are always smaller `O(n)`
``` ruby
class Integer
    MAX = 2^32
    MIN = -MAX
end

def isValid?(root, max, min)
    return 1 if root.nil?

    if (root.data <= min) || (root.data >= max)
        return 0
    end

    isValid?(root.left, root.data, min) & isValid?(root.right, max, root.data)
end

def isValidBST(root)
    isValid?(root, Integer::MAX, Integer::MIN)
end
```

```ruby
def isValidBST(root)
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

def getSuccessor(self, A, B):
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