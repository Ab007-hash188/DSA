c) Analysis
 
Heap structure and its height
Only Heap Sort builds an actual heap. With n=7, it's a complete binary tree of height floor(log2(7)) = 2 (3 levels). Quick Sort has no heap - just a recursion tree, which here had depth 3 (fairly balanced, since the pivots split the array reasonably evenly).
 
Number of comparisons/swaps observed
Metric        Heap Sort    Quick Sort
Comparisons   21           12
Swaps         18           6
 
Quick Sort did less work here because the pivots happened to split the array evenly (near its best case). Heap Sort's extra cost comes from building the heap plus a sift-down after every one of the 7 extractions.
 
Time complexity
- Heap Sort: O(n log n) in best, average, and worst case - consistent regardless of input order.
- Quick Sort: O(n log n) average/best, but O(n^2) worst case (e.g., sorted input with poor pivot choice).
 
Space requirements
- Heap Sort: O(1) - sorts in place, no recursion required.
- Quick Sort: O(log n) average (recursion stack), O(n) worst case.
 
Which approach suits the hospital's continuous-insert, always-need-highest-priority scenario?
Neither sorting algorithm fits directly - the hospital needs a dynamic priority queue (ongoing insert + repeated extract-max), not a one-time sort of a fixed dataset. The Max Heap (part a) is the correct structure: both insert and extract-max run in O(log n), it uses only O(n) space, and - unlike Quick Sort - its performance never degrades regardless of the order patients arrive in.
 
Conclusion: the Max Heap approach is the suitable one for the hospital's real-time priority queue, not a one-shot sort like Heap Sort or Quick Sort.
 
