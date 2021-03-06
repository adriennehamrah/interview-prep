## Time Complexity 
### Complexities 
- `O(n!)` - factorial - permutations
- `O(2^n)` - exponential - fibonacci, subsets
- `O(n^2)` - polynomial - bubble sort
- `O(nlogn)` - merge sort, quick sort (avg case)
- `O(n)` - linear 
- `O(logn)` - logarithmic - binary search
- `O(1)` - constant

#### O(n) (upper bound)

`f(x) = O(g(x))` (big-o): growth rate of `f(x)` is asymptotically <= growth rate of `g(x)`

`f(x) = o(g(x))` (little-o): growth rate of `f(x)` is asymptotically < growth rate of `g(x)`

#### Ω(n) (lower bound)

`f(x) = Ω(g(x))` (big-omega): growth rate of `f(x)` is asymptotically >= growth rate of `g(x)`

`f(x) = ω(g(x))` (little-omega): growth rate of `f(x)` is asymptotically > growth rate of `g(x)`

#### Θ(n) (tight bound) 

`f(x) = Θ(g(x))` (theta): growth rate of `f(x)` is asymptotically = growth rate of `g(x)`

#### Tips
- Check when variables are initialized/incremented - inside or outside loops
- Consider scenario when all input values are the same

##
