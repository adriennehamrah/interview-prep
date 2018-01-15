# Linked List
- Head and tail can either have value of `nil` or be sentinel nodes (dummy nodes that do not hold a value)
- Sentinel nodes avoids type checking for nil - simplier code for insertion and deletion.

## Reverse Linked List
``` ruby
def reverseList(a)
    current = a
    next_node = nil
    prev = nil

    while current != nil do
      next_node = current.next
      current.next = prev
      prev = current
      current = next_node
    end

    prev
end
```
## List Cycle - Return node where cycle beings
- Tortoise and hare (x, 2x speeds)
- Once intersection is found, start a pointer at the beginning and move at same speed. Find the intersection.

``` python
def detectCycle(self, A):
    slow = fast = A

    while True:
        if not(fast and fast.next):return None
        slow, fast = slow.next, fast.next.next
        if fast == slow: break

    slow = A

    while slow != fast: slow, fast = slow.next, fast.next
    return slow
```

## Delete kth Node from End of LL
- Use two pointers

``` ruby
def removeNthFromEnd(a, b)
    return a if (a.nil?)
    return nil if(a.next.nil? and b == 1)

    i = 0
    lead_node = a
    trailing_node = a

    while (lead_node && i < b)
        lead_node = lead_node.next
        i += 1
    end

    if(lead_node.nil? || lead_node.next.nil? )
        a = a.next
        return a
    end

    while lead_node.next
        lead_node = lead_node.next
        trailing_node = trailing_node.next
    end     


   delete_node = trailing_node.next
   trailing_node.next = delete_node.next
   delete_node = nil

   a
end
```

## Intersection of Two Linked Lists
- Find difference in lengths of two lists. Start pointers at same distance from end. Find where pointers are the same.
- Time: `O(n)`, Space: `O(1)`
``` Python
def getIntersectionNode(self, A, B):

    def length(l):
        len_list = 0
        while l:
            len_list += 1
            l = l.next
        return len_list

    lena = length(A)
    lenb = length(B)
    if lena > lenb:
        A, B= B, A
        d = lena - lenb
        lena, lenb = lenb, lena
    else:
        d = lenb - lena

    for i in range(d):
        B = B.next

    while A and B:
        if A == B:
            return A
        else:
            A = A.next
            B = B.next

    return None
```

## Partition Linked List
- Create two new pointer nodes - one from nodes smaller than b, one for nodes larger
``` ruby
   def partition(a, b)
        return a if a.nil? || a.next.nil?
        
        n1 = ListNode.new(-1)
        n2 = ListNode.new(-1)
        
        less = n1
        more = n2
        curr = a
        
        while curr
            if curr.data < b
                less = less.next = curr
            else
               more = more.next = curr
            end
            curr = curr.next
        end
        
        more.next = nil
        less.next = n2.next
        
        return n1.next
    end
 ```
