# Binary Search
## Count Number of Occurences of Element in a Sorted Array
- `O(logn)` time via binary search
- Find first and last index of occurence

```ruby
  def binarySearch(arr, target, first)
    result = -1
    low = 0
    high = arr.length - 1

    while low <= high
      mid = (low + high) / 2

      case arr[mid] <=> target
      when 0
        result = mid
        if first 
          high = mid - 1
        else 
          low = mid + 1
        end
      when 1
        high = mid - 1
      else
        low = mid + 1
      end
    end
    result
  end 
    
  def findCount(arr, target)
    first = binarySearch(arr, target, true)
    return 0 if first == -1

    last = binarySearch(arr, target, false)    

    last - first + 1
  end
 ```

## Rotated Sorted Array Search
- Find pivot point with binary search
- Compare first element in array, if target is larger, search in left side. Else search in right.
 
## Square Root of Integer
- Use binary search from 2 to A/2
- Check for 0 or 1 first
- If A is not a perfect integer, return the floor of the square root

```python
def sqrt(self, A):
    if A==0 or A==1:
        return A
    low = 2
    high = A/2
    
    while low <= high:
        mid = low + (high - low)/2
        
        if mid * mid == A:
            return mid
        elif mid * mid > A:
            high = mid - 1
        else:
            low = mid + 1

    if mid * mid > A:
        mid = mid - 1

    return mid
```
