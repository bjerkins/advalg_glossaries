% Fibonacci Heaps
* *CLRS Ch 19. You should be familiar with the potential method, described in Section 17.3, page 459 and the first half of page 460.*

# Definition
The data structure can be used for an algorithm like Dijkstra's algorithm where we continuously are going to use an extract minimum operation.

We can assume all nodes/values are different and therefore has an order. In case we will have to deal with bags containing doublets we could include its memory address for making them unique.

![The children are larger than their parents.](./figures/order.pdf)

![The roots in a layer are linked.](./figures/links.pdf)

![If we add a new node/value, it will simply be added in the top level.](./figures/add.pdf)

The amortized cost of the operations in a Fibonacci heap is 
<!-- The table with the operations -->
# Amortized Cost Proof
