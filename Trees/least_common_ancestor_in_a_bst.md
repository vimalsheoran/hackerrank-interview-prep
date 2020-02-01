# Least Common Ancestor in a Binary Search Tree.

[Problem Statement](https://www.hackerrank.com/challenges/binary-search-tree-lowest-common-ancestor/problem)

Least Common Ancestor (LCA) is a node which is the ancestor of two nodes. For a given node `x`, a node `n` is it's ancestor if there is a path from `n` to `x`. For two given nodes `x` and `y`, a node `n` is a **common ancestor** if there is a path from `n` to both `x` and `y`.

We solve this problem recursively. Using the following algorithm,
1. Check if both the nodes `x` and `y` can be reached from/searched from the current node. If yes, go to step 2, else, go to step 4. 
2. Now check if we can search/reach `x` and `y` from either of the left or the right child of the current node recursively.
3. If yes then the least common ancestor will be from the left or the right subtree, else the current node is the least common ancestor. Return the result.
4. Else return `NULL`

# Code

```cpp
// Auxiliary function for searching. Simple binary search.
bool search(Node *root, int value) {
	if (root == NULL) return false;
	if (root->data == value) return true;
	else if (root->data < value) return search(root->right, value);
	else return search(root->left, value);
}

Node* lca(Node *root, int x, int y) {
	// Check if the current node is an ancestor
	if (search(root, x) && search(root, y)) {
		// Now check if the left or the right child is an ancestor.
		Node* ancestor_l = lca(root->left, x, y);
		Node* ancestor_r = lca(root->right, x, y);
		// Return a common ancestor based on the search results.
		if (ancestor_l != NULL) return ancestor_l;
		else if (ancestor_r != NULL) return ancestor_r;
		else return root;
	} else return NULL;
}
```

**Time Complexity:** `O(nlogn)`