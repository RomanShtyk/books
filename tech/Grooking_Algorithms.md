#book Grooking algorithms by Aditya Y. Bhargava
7/10, must read for juniors and switchers. First half is for entry level, second half is a bit more
interesting, but lacks details.

Logs are the flip of exponentials.
Log always means log2 not log10 like in math (shit)

sorting objects - Timsort
sorting primitives - dual pivot quick sort

D&C works by breaking a problem down into smaller and smaller
pieces. If you’re using D&C on a list, the base case is probably an
empty array or an array with one element.

If you’re implementing quicksort, choose a random element as the
pivot. The average runtime of quicksort is O(n log n)!

The constant in Big O notation can matter sometimes. That’s why
quicksort is faster than merge sort.

The constant almost never matters for simple search versus binary
search, because O(log n) is so much faster than O(n) when your list
gets big.

If there’s a path, breadth-first search will find the shortest path.

Once you check someone, make sure you don’t check them again.
Otherwise, you might end up in an infinite loop.

Dijkstra’s algorithm only works with directed acyclic graphs, called DAGs for short.
You can’t use Dijkstra’s algorithm if you have negative-weight edges.

Bellman-Ford algorithm can work with negative weights

Greedy algorithms optimize locally, hoping to end up with a global
optimum.
• NP-complete problems have no known fast solution.
• If you have an NP-complete problem, your best bet is to use an
approximation algorithm.
• Greedy algorithms are easy to write and fast to run, so they make
good approximation algorithms.

Dynamic programming is useful when you’re trying to optimize
something given a constraint.
• You can use dynamic programming when the problem can be
broken into discrete subproblems.
• Every dynamic-programming solution involves a grid.
• The values in the cells are usually what you’re trying to optimize.
• Each cell is a subproblem, so think about how you can divide your
problem into subproblems.

Refresh:
• B-trees
• Red-black trees
• Heaps
• Splay trees
• Inverted indexes
• Bloom filters
• HyperLogLog
• sha/bcrypt
• Simhash
• Diffie-Hellman
• Simplex

![telegram-cloud-photo-size-2-5395829450928673248-y.jpg](..%2F..%2F..%2FLibrary%2FGroup%20Containers%2F6N38VWS5BX.ru.keepcoder.Telegram%2Fappstore%2Faccount-18037556929251400032%2Fpostbox%2Fmedia%2Ftelegram-cloud-photo-size-2-5395829450928673248-y.jpg)
