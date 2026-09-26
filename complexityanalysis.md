Complexity Analysis — Heap Sort vs Quick Sort
Time Complexity
Case	Heap Sort	Quick Sort
Best	O(n log n)	O(n log n)
Average	O(n log n)	O(n log n)
Worst	O(n log n)	O(n²)

Heap Sort: Building the heap from n elements takes O(n) time (not O(n log n), because most nodes are near the bottom and need little sifting). Each of the n extraction steps then costs O(log n) to re-heapify, giving n × O(log n) = O(n log n) overall. This holds in every case — best, average, and worst — because the heap's shape (a complete binary tree) never depends on the input's order, only on n.

Quick Sort: Each partition step costs O(n) comparisons. If the pivot splits the array roughly in half each time, there are O(log n) levels of recursion, giving O(n) × O(log n) = O(n log n) — this is both the best and average case (confirmed by our trace: pivots 85, 50, 30/72 split the array fairly evenly, costing only 12 comparisons). But if the pivot is always the smallest or largest element (e.g., an already-sorted array with last-element pivoting), each partition only removes one element, giving n + (n-1) + (n-2) + ... = O(n²) in the worst case.

Space Complexity
	Heap Sort	Quick Sort
Extra space	O(1)	O(log n) avg, O(n) worst

Heap Sort sorts in place using array-index arithmetic (2i+1, 2i+2) — no auxiliary array, and it can be written iteratively with no recursion stack, so it's O(1).

Quick Sort is usually implemented recursively; each recursive call adds a stack frame. With balanced partitions, the recursion depth is O(log n). With unbalanced partitions (worst case), depth can reach O(n).

Why This Matters for the Hospital

Heap Sort's guaranteed O(n log n) and O(1) space make it the safer, more predictable general-purpose sort — it never degrades no matter how patients happen to be ordered. Quick Sort is typically faster in practice (fewer comparisons, better cache locality) but carries worst-case risk on already-sorted or adversarial input.

However, neither is actually the right fit for the hospital's real requirement (continuous insertion + repeated extract-highest-priority). That workload needs the Max Heap structure itself, which gives O(log n) insertion and O(log n) extract-max, with no need to re-sort the whole dataset each time a new patient arrives.

Content
