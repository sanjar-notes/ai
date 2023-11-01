# 4. L17 - Populations Based Methods for optimization - 1
Created Saturday 17 October 2020

[../4._L17_-_Populations_Based_Methods_for_optimization_-_1.pdf](./4._L17_-_Populations_Based_Methods_for_optimization_-_1.pdf)
We try to solve TSP
Path representation - Vector of cities.

* Single point crossover does not work here.


*****

**PMX**(Partially managed crossovers)

1. Select two random points.
2. Copy a part of genes as it is.
3. Try to copy from the other parent, if it is possible(no repetition).
4. If copying is not possible, go to the one(in the same gene) which is redundant, and copy its vertical child neighbour.
5. Complete the procedure till the two children are over.

![](./4._L17_-_Populations_Based_Methods_for_optimization_-_1/pasted_image.png)


*****

**Order Crossover(OC)**:

1. Select two random points
2. Copy a part of genes as it is.
3. Fill the other two parts from the other parent in order

![](./4._L17_-_Populations_Based_Methods_for_optimization_-_1/pasted_image001.png)


*****

**Adjacency Representation**
It is vector with 1 based indexing where each value at ith index represents the next city for that index city.
![](./4._L17_-_Populations_Based_Methods_for_optimization_-_1/pasted_image002.png)
![](./4._L17_-_Populations_Based_Methods_for_optimization_-_1/pasted_image003.png)

* Not every adjacency list is a valid tour

![](./4._L17_-_Populations_Based_Methods_for_optimization_-_1/pasted_image004.png)
Observe the path representation: 1 → 2 → 1 (invalid)

* Advantage of adjacency representation - A single path in path repr can be written in n ways(by rotation). This is not the case with adjacency representation, where these 'n' equivalent paths have a single representation.

Doubt: Is the adjacency representation complete? - Yes. Any path repr is always convertible to adjacency repr.


*****

**Alternating Edge crossover(AEX)**
Used for adjacency representation
We alternate the source of gene from parent in each iteration. If it makes the child invalid, choose randomly from the parent(in current turn)
p1 = (5 1 7 8 4 9 6 2 3)
p2 = (3 6 2 5 1 9 8 4 7)
c1 = 5 1 9 6 2 3 7 8 4
c2 = 3 6 2 5 1 9 4 7 8


*****

**Heuristic crossover**
Select some starting gene, then the next city based the 6th city's next city.


*****

**Ordinal Representation**
Write the cities from 1 to n(in order).
For each in path repr, append the index(1-based) from the count list, ignoring the crossed one.
![](./4._L17_-_Populations_Based_Methods_for_optimization_-_1/pasted_image005.png)


