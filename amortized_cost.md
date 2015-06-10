% Amortized cost
In amortized cost we define an upper bound for the average cost for each operation. There are three different methods:

* Aggregation Cost
* Accounting method
* Potential Method

In **aggregation cost** we look at an upper bound for the total cost of a sequence of operations, $T(n)$. Then is the amortized cost for each operation the mean $$\hat{c} = \frac{T(n)}{n}.$$ Here each operation will have the same amortized cost.

In the **accounting methods**, we can add extra cost to some operations for 'paying' later for more expensive operations. 
Let say and operation $o_{i}$ costs $O(1)$ and and add additional 1 credit to the cost. If we can show that there will always be at least $n$ credits when another operation, $o_{j}$ costs $O(n)$. Then we can use the credit to pay for the operation and it will therefore end up having $O(1)$ in amortized cost.

Finally, **Potential method** uses a potential function for the data structure $\phi(D_i)$ that generates a real value where $D_i$ is the data structure at state $i$. It's required that $$\phi(D_i)\geq0$$ for all $i$.The amortized cost of a function is then $$\hat{c_i} = c_i + \phi(D_i) - \phi(d_{i-1})$$. 