# Project Name: Art Gallery Problem
Art Gallery is a well studied algorithm in the field of computational geometry. The problem models an art gallery as a simple polygon (with or without holes). The problem asks to find the smallest subset of vertices of V, such that each vertex of the subset has a visibility edge to every point inside the polygon.
In this repository, a common approximate approach to the Art Gallery Problem is illustrated.

## Concepts
The Art Gallery problem utilizes several concepts from graph theory and computational geometry. It can be shown that it is sufficient to place $\lfloor n/3 \rfloor$, and sometimes necessary to do so. The proof is evident from the concepts of triangulation and coloring.

### Triangulation
Triangulation of a simple polygon is the construction of triangles from the vertex set of a polygon, such that no two edges of a triangle cross-over. The triangles formed constitute a triangulation of a polygon. The below figure illustrates a simple example.
![triangulation](https://groups.csail.mit.edu/graphics/classes/6.838/F01/lectures/PolygonTriangulation/triangulation.gif)

As evident, there are several ways we can triangulate a polygon. The exact number of ways we can triangulate a polygon is given by the (n-2) Catalan number.

#### Algorithm
Triangulation of a polygon is a well studied problem. The best known algorithms run in O(nlogn). In this implementation, we employ the ear-clipping algorithm for triangulating the entire polygon.

An ear vertex of a polygon is a vertex whose triangle with it's 2 neighbour vertices does not enclose any other vertex of the polygon. These vertices are used in the clipping algorithm as follows.
* Classify each vertex of the polygon as either reflex, convex or ear vertex.
For n-3 iterations, do the following
* Pick an ear vertex at random, and it along with its 2 neighbours to the list of triangulated points.
* Update the vertex status of each of it's neighbours
* Repeat the above steps

The correctness of the algorithm above relies on the below theorem.

**Theorem** : Every n-sided simple polygon, has atleast 2 ear vertices. This is because each triangle created by an ear clip operation contains exactly one ear vertex.

The time complexity of the triangulation algorithm is $O(n^2)$, where n is the number of vertices of the polygon.

### Graph Coloring
Graph coloring is the process of coloring (or assigning a category) to each of the vertices of a graph. The [3-coloring of a graph](http://www.cs.toronto.edu/~lalla/373s16/notes/3col.pdf) is a known NP-complete problem. However, there are certain classes of graphs that can be colored more efficiently, i.e in polynomial time.

The traingulation of the polygon as described above, generates a chordal graph. Chordal graphs, are a class of graphs where in, if the graph consists of a cycle of length 4 or more nodes, then there will exist a chord in between them.

#### Algorithm
For the chordal graph obtained, we employ a perfect elimintaion ordering mechanism.
* A random node is chosen as start node, and a random neighbour is chosen as well. The two nodes are colored using two available options.
* A queue of node pairs are created, and as long as the queue has elements, a set of all common neighbours are obtained. These neighbours are third colored, if not already colored and the first, third node pair and the second, third node pair is added to the queue.

The above Graph coloring of chordal graphs is done in $O(N+E)$ time.

## Variations
The Art Gallery problem has many real world applications in the field of robotics and communications. For this reason, several extensions of the problem have been posed and studied in the last few decades. For instance, there have been variations such as the watchman route problem, which studies the shortest path a a guard has to take to cover the entire interior of the polygon. This problem has motivated many scientists to study properties of graphs and vertex sets such as dominating sets and independent sets. Another variation to the problem is that of an optimzation problem. The problem asks to find the least number of guards to place on the vertex set, such that a security score is maximized. The security score could be defined as a polynomial function such as the inverse of the distance between interior of points and the verices, or just the sum of vertices that are also endpoints of a visibility edge.

## Steps
Ear Clipping Algorithm for triangulating a simple polygon P
The triangulated polygon is represented as a chordal graph
Every chordal graph is 3-colorable in O(N) time, where N is the number of vertices.

## Usage
Run the Jupyter notebook to view the results

## Contact Information
Email: <nrvinay08@gmail.com> and <k.rachna27@gmail.com>
