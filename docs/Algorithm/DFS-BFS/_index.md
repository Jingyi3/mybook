---
weight: 10
---

# DFS BFS
A Tree is typically traversed in two ways:

**BFS** Breadth First Traversal (Or Level Order Traversal)
**DFS** Depth First Traversals
- Inorder Traversal (Left-Root-Right)
- Preorder Traversal (Root-Left-Right)
- Postorder Traversal (Left-Right-Root)

## Time & Space
Is there any difference in terms of **Time Complexity**?  
All four traversals require O(n) time as they visit every node exactly once.

Is there any difference in terms of **Extra Space**?  
There is difference in terms of extra space required.  
1. Extra Space required for Level Order Traversal is O(w) where w is maximum width of Binary Tree. In level order traversal, queue one by one stores nodes of different level.
2. Extra Space required for Depth First Traversals is O(h) where h is maximum height of Binary Tree. In Depth First Traversals, stack (or function call stack) stores all ancestors of a node.

**It is evident from above points that extra space required for Level order traversal is likely to be more when tree is more balanced and extra space for Depth First Traversal is likely to be more when tree is less balanced.**

## How to Pick One?

1. Extra Space can be one factor (Explained above)  
2. Depth First Traversals are typically recursive and recursive code requires function call overheads.  
3. The most important points is, BFS starts visiting nodes from root while DFS starts visiting nodes from leaves. So if our problem is to search something that is more likely to closer to root, we would prefer BFS. And if the target node is close to a leaf, we would prefer DFS.  
