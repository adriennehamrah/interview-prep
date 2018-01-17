# Trees
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
