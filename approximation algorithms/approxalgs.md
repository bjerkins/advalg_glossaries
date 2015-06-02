% Approximation algorithms

Algorithms that return near-optimal solutions in polynomial time. 

## Vertex cover problem

$G = (V,E)$, vertex cover is a subset $V' \subseteq V$, such that if $(u,v) \in E$ then either $u \in V'$, $v \in V'$ or both. Size of the vertex cover is the number of vertices in $V'$. _Optimal vertex cover_ is a vertex cover of minimum size in a given undirected graph. 

**APPROX-VERTEX-COVER**

We don't know how to find an optimal vertex cover in polynomial time, but the **approximation algorithm** returns a vertex cover with size guaranteed to be nore more than twice the size of an optimal one _(2-approximation algorithm)_. The running time for this approximation algorithm is $O(V + E)$.

The approximation algorithm does the following: 

1. Choose an arbitrary edge in the graph. 
2. Remove the edges of the incident vertices $u, v$, to that edge
3. Collect $u, v$ together, which eventually forms the vertex cover.

**Proof** 

We denote $A$ to be the set of the edges that were picked arbitrarly. To cover all the edges in this set, any vertex cover and in particular the optimal cover $C^{\star}$ must include at least one endpoint vertex of each edge in A. Since we remove all the incident edges from the endpoints that form the edge we picked, no edge in $A$ share the same endpoint. This means that no two edges in $A$ are covered by the same vertex from $C^{\star}$, giving us the lower bound:

$$|C^{\star}| \geq |A|$$ 

and since we pick an edge which neither of its endpoints are in $C$ (_since we removed the incident edges!_), we have an exact upper bound for the vertex cover returned:

$$|C| = 2|A|$$

which implies:

$$ |C| \leq 2 |C^{\star}|$$

---

## The traveling-salesman problem

Given a complete, undirected graph $G = (V, E)$ that has non-negative cost function $c(u,v)$ associated with each edge $(u,v) \in E$, we find a Hamiltonian cycle of G with minimum cost. 

**Triangle Inequality**

$$ c(u,w) \leq c(u,v) + c(v,w) $$

**APPROX-TSP-TOUR**

`APPROX-TSP-TOUR` is a polynomial-time 2-approximation algorithm for the traveling-salesman problem with the triangle inequality:

1. Select a vertex $r$ from V to be the "root" vertex.
2. Compute the minimum spanning tree $T$ in $G$ starting in the root $r$.
3. $H$ lists the vertices in a visiting order from the preorder tree walk of $T$. We can use the preorder walk given the triangle inequality method. 
4. return the hamiltonian cycle H.

**Proof**

Let's denote the optimal tour for the given vertices as $H^{\star}$. We can obtain a spanning tree by deleting any edge from that tour where each cost is non-negative. A minimum spanning tree, $T$ from step 2, thus provides a lower bound on the cost for the optimal tour:

$$ c(T) \leq c(H^{\star}) $$

As step 3 says, we use preorder tree walk to list the vertices in the approximated tour. But before doing the preorder walk, a **full walk** $W$ listed each vertices each time the walk visited a vertex. The full walk visits every vertex twice giving:

$$ c(W) = 2c(T) $$

which we can imply that:

$$ c(W) \leq 2c(H^{\star})$$

However, the full walk $W$ isn't a tour since it visits some vertices more than once. But no worries, given the triangle inequality, we can delete re-occurring vertices in $W$ without having the cost to increase (_Deleting $v$ from $W$ between $u$ and $w$ results going straight from $u$ to $w$ which is less than or equal given the triangle inequality_). 

So, removing all but the first visit to each vertex from $W$ we obtain the preorder walk of $T$. We call the cycle corresponding to this walk $H$ and this is a hamiltonian cycle since every vertex is visited only once and this is the cycle that the approximation algorithm computes. Since we delete vertices from $W$, we have:

$$ c(H) \leq c(W) $$

which implies that:

$$ c(H) \leq 2c(H^{\star}) $$

---

## The set-covering problem
















