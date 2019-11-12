#### 11/12/19

#### PageRank
- The founding idea for Google
- web crwaler: get an initial graph out of all the pages they searched
- If a page is linked to another page, that page is also thrown into the map as well
- **_refer to handout_**


#### Binary Search Trees (BST)
- AVL Tree is a specific type of BST
- the height of the tree is the worst case scenario (runtime) for any type of operations on a BST
	- Theta(h)
- Adding to a BST
	- find where it should be, then add it as a leaf node
- If always jumping to the middle value, will get the best balanced tree
- Remove from a BST
	1. find it
	2. if a leaf node, delete it
	3. if not a leaf node, find the predecessor or successor, swap them, delete that node (if it's a leaf node)
		- predecessor: the right-most node in the left sub-tree
		- successor: the left-most node in the right sub-tree
	4. if not a leaf node, it has one child; _promote_ that child (the grandparent adopts that child)
		- predecessor: has no child or has only a left child (or else that right child would have been the predecessor)
		- successor: has no child or has only a right child (or else that left child would have been the successor)
**AVL Trees**
- No matter what order you add the data, it will always be a balanced tree
- opposite end on the data struture spectrum as the heap
- flexibility in determining what the structure is, but once that is determined, there's only one way the data can go
- it is a BST
- every node meets the **height-balance property**
	- the height of the left subtree is within +/- 1 of the right subtree

**Good Data Structure**
- some degree of flexibility and restrictions
- sorted array is BAD data structure