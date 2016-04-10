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
