Download Link: https://assignmentchef.com/product/solved-ds-lab10-minimum-spanning-tree
<br>
In the previous lab, we learned graph and how to traverse it. In this lab, we will learn a problem of graph is Minimum Spanning Tree. To find the Minimum Spanning Tree, we have two basic algorithms:

<ol>

 <li>Prim’s algorithm</li>

 <li>Kruskal’s algorithm</li>

</ol>

<h1>1.      Minimum Spanning Tree</h1>

Tree <strong>T </strong>is a connected graph that has V vertices and V‐1 edges, only one unique path between any two pair of vertices in T.

Given connected graph <strong>G </strong>with positive edge weights, find a min weight set of edges that connects all of the vertices.

Figure 1: Graph

A spanning tree of a graph G is a subgraph T that is connected and acyclic.                                                                                                             <strong>1</strong>

Figure 2: Minimum Spanning Tree

<h1>2.      Prim’s Algorithm</h1>

The way Prim’s algorithm works is as follows :

<ul>

 <li>Initialize the minimum spanning tree with a initial vertex.</li>

 <li>Find all the edges that connect the tree to new vertices, find the minimum, and add it to the tree.</li>

 <li>Keep repeating step 2 until we get a minimum spanning tree (until all vertices are reached).</li>

</ul>

You can follow this instruction to step by step implement Prim algorithm: 1. Create a boolean array (visited[]) and two integer arrays (parent[], cost[])

<ol start="2">

 <li>Choose the initial vertex.</li>

 <li>Find the vertex which has the minimum cost from the latest vertex and hasn’t been visited (we can call this vertex is min_id).</li>

 <li>Set visited[min_id] = true</li>

 <li>Update parent[] from min_id to the vertices which haven’t visited. Update cost[] if the cost from new vertex is smaller than from the previous.</li>

 <li>Repeat step 3 until all vertices are visited.</li>

</ol>

<h1>3.      Kruskal’s Algorithm</h1>

To simplify Kruskal’s implementation, we will you <strong>Edge List </strong>to store the graph. The steps for implementing Kruskal’s algorithm are as follows:

<ol>

 <li>Sort all the edges from low weight to high.</li>

 <li>Take the edge with the lowest weight and add it to the spanning tree. If adding the edge created a cycle, then reject this edge.</li>

 <li>Keep adding edges until we reach all vertices.</li>

</ol>

To check the edge created a cycle or not, you can <strong>Union-Find Disjoint Sets</strong>.

This is Union-Find code, you can init an instance and use isSameSet(int i, int j) method to check two vertices i, j create a cycle or not.

<table width="529">

 <tbody>

  <tr>

   <td width="529">class UnionFind{private Vector&lt;Integer&gt; p, rank, setSize;public UnionFind(int N) { p = new Vector&lt;Integer&gt;(N); rank = new Vector&lt;Integer&gt;(N);setSize = new Vector&lt;Integer&gt;(N); for (int i = 0; i &lt; N; i++) {p.add(i); rank.add(0); setSize.add(1);}}public int findSet(int i) { if (p.get(i) == i) return i;else { int ret = findSet(p.get(i)); p.set(i, ret);return ret;}}public void unionSet(int i, int j) { if (!isSameSet(i, j)) { int x = findSet(i), y = findSet(j); if (rank.get(x) &gt; rank.get(y)) {p.set(y, x);setSize.set(x, setSize.get(x) + setSize.get(y));} else{p.set(x, y); setSize.set(y, setSize.get(y) + setSize.get(x)); if (rank.get(x) == rank.get(y))rank.set(y, rank.get(y) + 1);}}}public boolean isSameSet(int i, int j){ return findSet(i) == findSet(j);}}</td>

  </tr>

 </tbody>

</table>

1

2

3

4

5

6

7

8

9

10

11

12

13

14

15

16

17

18

19

20

21

22

23

24

25

26

27

28

29

30

31

32

33

34

35

36

37

38

39

40

41

42

43

44

45

<h1>4.      Exercise</h1>

Given a graph:

Read this graph from a text file with Adjacency Matrix.

<ul>

 <li>Write the Kruskal function for the given graph. Print MST result on the screen.</li>

 <li>Write the Prim function for the given graph starting from vertex 0. Print MST result on the screen.</li>

</ul>

<h1>5.      Reference</h1>

<ol>

 <li>https://www.cs.princeton.edu/courses/archive/spr07/cos226/lectures/mst.pdf</li>

 <li>https://www.journaldev.com/43746/prims-algorithm-minimum-spanning-tree-java</li>

</ol>

THE END