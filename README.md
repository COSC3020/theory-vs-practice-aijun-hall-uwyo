# Theory vs. Practice

- List 3 reasons why asymptotic analysis may be misleading with respect to
  actual performance in practice.

Asymptotic analysis may be misleading with respect to actual performance in practice, due to the fact it reduces information by design. Asymptotic analysis focuses on te growth rate as the input size increases to relatively large values. This means naturally that more granular information about an algorithm's performance will be lost. For example an analysis such as `O(1n^2 + 2n + 3)` simplifies to `O(n^2)` since lower order terms are ignored. Most of the time this doesn't mean much, but it still means information is being lost.

Another aspect that could be misleading to actual performance is that asymptotic analysis defines different performance scenarios. If you assume for example, a best-case
or average-case complexity when real data typically triggers worst-case behavior, then the predictions will be off. The analysis isn't incorrect, but the
scope of the scenario and the actual distribution of inputs can lead to misleading conclusions.

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
binary tree, we would see an assumption of `O(h) = O(n)` since an unbalanced tree is essentially the same datastructure as a linked list. 

The search algorithm itself within the binary search tree complete implementation might not be written as efficiently as possible, and could be using a different, worse time complexity to index and search for elements within the tree.

<hr>
Used https://www.geeksforgeeks.org/complexity-different-operations-binary-tree-binary-search-tree-avl-tree/ as reference for binary search tree performance. Referenced it for `O(h`) = O(log(n))`
<br><br>
I certify that I have listed all sources used to complete this exercise, including the use of any Large Language Models. All of the work is my own, except where stated otherwise. I am aware that plagiarism carries severe penalties and that if plagiarism is suspected, charges may be filed against me without prior notice.
