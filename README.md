# Theory vs. Practice

- List 3 reasons why asymptotic analysis may be misleading with respect to
  actual performance in practice.

Asymptotic analysis may be misleading with respect to actual performance in practice, due to the fact it reduces information by design. Asymptotic analysis focuses on te growth rate as the input size increases to relatively large values. This means naturally that more granular information about an algorithm's performance will be lost. For example an analysis such as `O(1n^2 + 2n + 3)` simplifies to `O(n^2)` since lower order terms are ignored. Most of the time this doesn't mean much, but it still means information is being lost.

Another aspect that could be misleading to actual performance is that asymptotic analysis ignores implementation details and language-level overhead. An algorithm that has a theoretical optimal time complexity in one language could be different in another language, or even in the same enviornment with different packages due to factors like library calls, runtime features (garbage collection), and multi-threading. Asymptotic analysis does not factor in external factors such as these.

Finally, the underlying physical hardware is also taken out of the equation with asymptotic analysis. If a machine that an algorithm is running on can not keep up with the demand in computing resources like ram or storage, then it will be bottlenecked in reality. Or on an extreame level enviornmental factors like bitflips and bad hardware can also cause unpredictability in real algorithm perfomance.

- Suppose finding a particular element in a binary search tree with 1,000
  elements takes 5 seconds. Given what you know about the asymptotic complexity
  of search in a binary search tree, how long would you guess finding the same
  element in a search tree with 10,000 elements takes? Explain your reasoning.

A binary search tree has an asymptotic complexity of `O(h)` where `h` is the height of the tree such that then the runtime is `O(log(n))` to search for an element, since the number of nodes in the binary search tree is `2^h - 1`.

Log base 2 of 1000 = 9.965784285. This is the height of a tree with 1000 elements
Log base 2 of 10000 = 13.28771238. This is the height of a tree with 10000 elements

A height increase percentage from `n = 1000` to `n = 10000` is ` 13.28... / 9.96... = 1.33`

If `n = 1000` takes 5 seconds, then `5 * 1.33 = 6.65` seconds for `n = 10000`

- You measure the time with 10,000 elements and it takes 100 seconds! List 3
  reasons why this could be the case, given that reasoning with the asymptotic
  complexity suggests a different time.

The machine running the algorithm could be subject to hardware limitations. In a scenario where at smaller input sizes, the algorithm fits comfortable in cache or RAM, but at 10,000 elements it exceeds memory thresholds, this could force the system to swap data to disk or cause more frequent garbage collection. This is an example of
a runtime being dramatically slowed down by something that wouldn't manifest at lower input sizes.

The binary search tree might also not be balanced, which would result in the assumption of `O(h) = O(log(n))` being incorrect. In the case of an unbalanced
binary tree, we would see an assumption of `O(h) = O(n)` since an unbalanced tree is essentially the same datastructure as a linked list. In the case of this question it is stated that `n = 10000` took `100 seconds`. In the previous runtime of `O(log(n))`, we can find out how long it takes to do 1 operation with $\frac{5 seconds}{ln(1000)} = 0.724\ \text{seconds}$.

Now: $0.724 * 10000 \ \text{elements} = 7240 \ \text{seconds}$ for an expected worst case scenario runtime of 7240 seconds. This worst case scenario assumes that the tree is 100% unbalanced and acts exactly like a linked list so it is much larger than a runtime of the previous `6.65` for `O(log(n))`, which would instead imply at least some amount of sorted data within the tree. A best case scenario runtime analysis would therefore be $0.724 * 1$ = 0.724 (within the hypothetical situation that the tree is unbalanced) seconds since this case assumes the first element is the element attempted to be searched for at the top of the tree. An average case runtime could therefore be anywhere between 0.724 seconds and 7240 seconds, with 2 data points given to us previously that `n = 1000` -> 5 seconds, and `n=10000` -> 100 seconds. A runtime of 100 seconds at `n=10000` therefore implies there is at least some amount of sorted data within the tree. 

The search algorithm itself within the binary search tree complete implementation might not be written as efficiently as possible, and could be using a different, worse time complexity to index and search for elements within the tree.

<hr>
Used https://www.geeksforgeeks.org/complexity-different-operations-binary-tree-binary-search-tree-avl-tree/ as reference for binary search tree performance. Referenced it for `O(h`) = O(log(n))`
<br><br>
I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.
