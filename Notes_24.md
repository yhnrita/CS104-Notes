#### 9/19/19

#### Splay Tree
- a BST with special operations
- optimized average case runtime
- works really well on real data
- does _NOT_ guarantee balance
- no priority, the last thing you access is guaranteed to be at the root
- the last thing you access x calls ago will be guaranteed to be within 2x height of the root
- The 90/10 rule
	- 90% of the wealth tend to be controled by 10% of the people
	- human behavior tend to fall under this rule
	- if you just did an operation on a piece of data, it's likely you will use it very soon
- guaranteed Theta(n) for all operations, but great average case
- Exioms
	1. Always move the last thing you find at the top
	2. Whenever you make a way down the path, leave it in a better state than you found it
- **Insert**
	1. insert using the normal BST insert
	2. "splay" to the top
	- **_Rotation graphs refer to handout 24_**
- If you have a really bad Splay Tree, it's because the previous operations are all very cheap (Theta(1))
- Splay Trees guarantee average case Theta(log n) and amortized Theta(log n)
- If using completely random data and care about the guarantees, use AVL Trees; if using data reflecting the 90/10 Rule and amortized is good enough, then use Splay Tree
- **Delete**
	- _HAS_ to splay the path (to leave the tree in a better state)
	1. delete the node
	2. take the parent of that node and splay it to the top
- Makes the path you just traversed better at the cost of other paths
- The "Splay Trees Are Awesome" Conjecture: For _any_ sequence of operations starting on an empty tree, a splay tree is no more than a constant factor worse than _any_ BST implementation

