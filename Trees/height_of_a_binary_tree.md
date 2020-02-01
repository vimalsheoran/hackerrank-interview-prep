# Height of a Binary Tree
[Problem Statement](https://www.hackerrank.com/challenges/tree-height-of-a-binary-tree/problem)

Height of a binary tree is given as Total number of nodes in the longest path - 1 .Height of a binary tree can be easily found using a recursive approach. The idea is to calculate the height of the left sub-tree and the right sub-tree, the maximum of these two values will the height of the given tree. The base case for recursion here, is that the height of the tree with a single node is zero.

# Code

The `calculate_height()` function will calculate the height of the binary tree, it takes one parameter which is the `root` node.

```cpp
int calculate_height(Node *root) {
	// Base case for recursion in case there is only a single node or a leaf node.
	if (root->left == NULL && root->right == NULL) return 0;
	// Find the height of the left and right sub-trees recursively.
	int height_l = calculate_height(root->left);
	int height_r = calculate_height(root->right);
	// Current height will be 1+ the max of the heights of the left and right sub-trees.
	return 1+max(height_l, height_r);
}
```