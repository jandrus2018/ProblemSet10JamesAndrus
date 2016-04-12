# ProblemSet10JamesAndrus
##hasEdge() Method
```
	public boolean hasEdge(int v, int w) {
		validateVertex(v);
		validateVertex(w);
		for (int a : adj[v])
			if (a == w)
				return true;
		return false;
	}
```
##Testing of hasEdge() Method
```
	public static void main(String[] args) {
		Graph G = new Graph(4);
		G.addEdge(0, 1);
		G.addEdge(0, 2);
		G.addEdge(0, 3);
		G.addEdge(1, 1);

		System.out.println(G.hasEdge(3, 0));
		System.out.println(G.hasEdge(3, 1));
		System.out.println(G.hasEdge(0, 3));
		System.out.println(G.hasEdge(2, 3));
		System.out.println(G.hasEdge(1, 1));
```
##4.1.24 Computation of number of connected Components,
##size of largest component, and number of components 
##size less than 10.
```
	public static void main(String[] args) {
		SymbolGraph sg = new SymbolGraph("F:/MISC/movies.txt", "/");
		Graph G = sg.G();
		CC cc = new CC(G);

		// uses count method to report the number of connected components
		int M = cc.count();
		System.out.println("movies.txt contains " + M + " connected components");

		// makes a queue of queues, with each queue corresponding to a connected
		// component, so we can analyze the size of each connected component
		Queue<Integer>[] components = (Queue<Integer>[]) new Queue[M];
		for (int i = 0; i < M; i++) {
			components[i] = new Queue<Integer>();
		}
		for (int v = 0; v < G.V(); v++) {
			components[cc.id(v)].enqueue(v);
		}

		// initialize three variables to keep track of the largest element,
		// components of size less than 10, and the total number of vertices
		// respectively
		int largest = 0;
		int counterL10 = 0;
		int sum = 0;

		// go through the queue of connected components to find largest
		// component, components of size less than 10, and the sum of the
		// vertices
		for (int i = 0; i < M; i++) {
			int size = components[i].size();
			if (size > largest)
				largest = size;
			if (size < 10)
				counterL10++;
			sum += size;
		}

		// if all the vertices are accounted for, report the largest, and number
		// of components of size less than 10
		if (sum == G.V()) {
			System.out.println("All " + sum + " vertices accounted for.");
			System.out.println("Largest component has size " + largest);
			System.out.println("Number of components size < 10 is " + counterL10);
		}

	}
```
