# Leetcode-637.-Average-of-Levels-in-Binary-Tree
# Description
Given the root of a binary tree, return the average value of the nodes on each level in the form of an array. Answers within 10-5 of the actual answer will be accepted.
 # Solution
Given a binary tree, calculate the average value of all nodes at each level (row) of the tree and return these averages in a list.

Key Points:

Binary Tree: A tree structure where each node has at most two children (left and right)

Level: Each horizontal row of the tree (root is level 0, its children are level 1, etc.)

Average: For each level, calculate (sum of all node values) ÷ (number of nodes at that level)

Precision: Results must be accurate within 0.00001

Example:

Input: root = [3,9,20,null,null,15,7]

Output: [3.00000,14.50000,11.00000]

Explanation: The average value of nodes on level 0 is 3, on level 1 is 14.5, and on level 2 is 11.
Hence return [3, 14.5, 11].
 # Algorithm
 1. Create empty list to store level averages
 2. Create queue and add root node
 3. While queue is not empty:  a. Get current level size (number of nodes at this level)          b. Initialize sum for current level = 0
 4. For each node in current level: Remove node from queue front and Add node value to level sum
 5. Add left child to queue (if exists) . Add right child to queue (if exists)
 6. Divide level sum by level size . Add average to result list
 7. Return list of averages
 # Code
from collections import deque
class Solution:

    def averageOfLevels(self, root: Optional[TreeNode]) -> List[float]:
        avgs=[]
        q=deque()
        q.append(root)

        while q:
            avg=0
            n=len(q)
            for _ in range(n):
                node=q.popleft()
                avg+=node.val
                
                if node.left:
                    q.append(node.left)
                if node.right:
                    q.append(node.right)
            avg/=n
            avgs.append(avg)
        return avgs 
 # Complexity
 Time Colmplexity:

 Each node is processed exactly once: Every node in the tree is visited and dequeued exactly one time

 Therefore:  O(N)

 Space Complexity:

 Queue storage: The queue stores at most one complete level at any time

 Result list: O(H) where H = height of tree (number of levels)

Variables: O(1) for temporary variables (sum, count, etc.)
