#### 11/14/19

#### AVL Trees
- **_refers to handout #23_**
- useful data strucutre for any application
- based upon BSTs
	- do anything to AVL tress, do the same thing to the BST, and then balance it
	- AVL tress are balanced BSTs
- **Deletion of BST**
	1. find it
	2. if leaf node, delete it and done
	3. if not, promote either the predecessor or successor, and delete that instead
	4. if has a child, promote it (adopt by the grandparent)
- AVL Tree: a BST where
	- for every node, the height of its left child is within 1 of its right child
- Balanced enough? Yes!
	- f(h) = the minimum # of nodes to produce a height h AVL tree
	- f(h) = f(h-1) + f(h-2) + 1 //the 1 root node
	- f(h) > 2f(h-2)
	- n > 2 ^ (h/2) //n = number of nodes
		- log n > h/2
		- 2 log n > h //h is upper bounded by 2 log n
	- **find(v)** takes Theta(log n) _guaranteed_
- Insertion and Deletion is the exact BST operations but with height updates & rotations
- **Insert**
	- add a node
	- **_Every node will store a height_**
	- visit its direct ancestors, update its height, until reaches one that does not need to be updates
	- OR encounter an unbalance
		- the unbalanced node rolls down, its higher node rolls up w/all its children
	- Z is the unbalanced node, Y is the taller subtree of Z, X is the taller subtree of Y
		- **Y is guaranteed to be the ancestor of the added node**
	- **Single Rotation** on handout
		- only works if you have Z-Y-X in same direction (Zig-Zig orientation)
		- ex. Y is right child of Z, and X is right child of Y
		- After rotate, the parent of the subtree that rotated does _not_ need to do anything
		- Only **_one_** rotation needed
	- **Double Rotation** on handout
		- only works if you have Z-Y-X is in a Zig-Zag orientation
		1. un-zig the zag
		2. do a single rotation
	- Guaranteed Theta(log n) //only need to find it, everything else is constant
- **Delete**
	- First call the BST delete property
	- visit its direct ancestors, update its height, until reaches on does not need to be updated/unbalance
	- Z is the unbalanced node, Y is the taller subtree of Z, X is the taller subtree of Y
		- **Y is guaranteed to _NOT_ be the tree which a node is deleted**
		- If Y has two subtrees that are of same height, do the **Single Rotation** instead of a Double Rotation
	- One rotations might _NOT_ be enough
		- Needs to keep going up and keep rotating until reaches a node that:
			1. does not need to be updated
			2. reaches the root
- All three major operations run in Theta(log n)
	1. Find
	2. Insert
	3. Remove










