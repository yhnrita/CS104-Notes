#### 10/24/19

#### Graphs
- G = (V, E)
	- |V| = n
	- |E| = m
- Graphs can only capture pairwise relationships
- Hypergraphs
	- Hyperedges
	- Won't be dealing with them
**Graph ADT**
1. Add a node
2. Delete a node
3. Add an edge
4. Delete an edge
5. Test if edge exists
6. Enumerate all outgoing edges from a node
- Commonly, there will be a stable set of nodes that will never be modified
	- nodes should be stored in a vector
	- nodes should be named 0:(n-1)
- _______________| Unsorted Array (Linked List) |  Sorted Array
	Add edge     |    Theta(1)	  				|	Theta(m)
   Delete edge   |    Theta(m)	  				|	Theta(m)
    Test edge    |    Theta(m)	  				|	Theta(log m)
  Enumerate edges|    Theta(m)	  				|	Theta(log m + (d^+)(v) <= outgoing edges from v

- _______________| Adjacency List  | Adjacency Matrix
	Add edge     |    Theta(1)	   |	Theta(1)
   Delete edge   | Theta((d^+)(v)) |	Theta(1)
    Test edge    | Theta((d^+)(v)) |	Theta(1)
  Enumerate edges| Theta((d^+)(v)) |	Theta(n)

__*Refer to Handout 17*__
- **Adjacency List**
	- a vector of linked lists to track all outgoing edges
	- will have a separate vec
	- Great if need to enumerate edges frequently
- **Adjacency Matrix**
	- a 2D matrix for booleans
	- Great if testing edges frequently
	- will be symmetric if the graph is undirected
	- diagonal should all be 0 if a simple graph (no self-loops)
	- high memory usage can lead to slower runtime

- If a graph is _sparse_ (m = O(n))
	- use an Adjacency List
	- the average number per node is constant
	- _trees_ are sparse
- If a graph is _dense_ (m = Theta(n^2))
	- use an Adjacency Matrix
	- the max number of edges can have is n(n-1)
	- an average number n edges leads to Adjacency List losing its advantage

#### Graph Search
- Is there a _path_ between two nodes?
- Do we find the shortest path or doesn't care?

**Breadth First Search (BFS)**
- Find the shortest path (in edges) from u to v
	- Layer 0 = node u
	- Layer 1 = all nodes w/ a direct edge from u
	- Layer 2 = exactly nodes w/ an edge from a node in layer 1, excluding node already in a previous layer
```c++
	int d[n]; //distance/layer
	int p[n]; //parent array, previous node, path
	bool v[n]; //visited

	void BFS(int u) {
		queue x;
		d[u] = 0;
		x.add(u);
		while(x is not empty) { //use Adjacency List
			int v = x.remove(); //FIFO
			for(all outgoing edges (v, w) from v) {
				if(!v[w]) {
					d[w] = d[v] + 1;
					p[w] = v;
					v[w] = true;
					x.add(w);
				}
			}
		}
	}
```
- Runtime: Theta(m + n)
	- Best to find the shortest path

**Depth First Search (DFS)**
- Will find you _a_ path if there is one
```c++
	int d[n]; //distance/layer
	int p[n]; //parent array, previous node, path
	bool v[n]; //visited

	void DFS(int u) {
		for(all outgoing edges (u, w) from u) {
			if(!v[w]) {
				v[w] = true;
				d[w] = d[u] + 1;
				p[w] = u;
				DFS(w);
			}
		}
	}
```
- Runtime: Theta(m + n)
- Advantage: intuitive
- a form of recursion: backtracking
- useful to find _all_ things









