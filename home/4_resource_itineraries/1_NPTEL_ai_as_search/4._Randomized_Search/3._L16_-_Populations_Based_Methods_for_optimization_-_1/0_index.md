# 3. L16 - Populations Based Methods for optimization - 1
Created Saturday 17 October 2020

In Hill climbing, or simulated annealing we are working with only one solution at any point of time. GAs are algorithms actually work with a set of candidate solutions.

Benefits of population based algorithms are:

1. Speed is increased considerably
2. Solutions can interact to produce better solutions
3. Seem to work better for real world problems, which have many jagged surfaces.



* Human brain is a very good example of emergent behavior - the elements being neurons.
* One difference between GAs and nature is that in GAs, fitness criteria is predetermined(by the fitness function), while in real life, fitness is an attribute that can only be assigned after an individual persists.


*****

**Conway's game of life**
The world is a 2D grid. Each cell represents room with a creature. A creature is said to be in a room if it is "ON" or "black" or "1". There are rules for being born and for dying.

* Many interesting patterns emerge in the grid.
* Some patterns oscillate, some die out, and some move around in the grid.
* This is a very good example of emergent behavior



*****

Example of running GA(numerical)

* Goal - get all 1's for a bit-vector of length 5
* Fitness function = (int(c))^2^
* Single point crossover operator
* n = 4, k = 4 , population remains constant
* No mutation


Step 0: Initial population
![](./3._L16_-_Populations_Based_Methods_for_optimization_-_1/pasted_image.png)
Here P = probability = f(x)/∑f(x)
Expected value, E = n*P
Step 1: Selection based on roulette wheel, determined by experiment
![](./3._L16_-_Populations_Based_Methods_for_optimization_-_1/pasted_image001.png)
Step 2: cross over
![](./3._L16_-_Populations_Based_Methods_for_optimization_-_1/pasted_image002.png)
Step 3: Mutation avoided

* Average fitness = ∑f(x)/n = 293(original)

![](./3._L16_-_Populations_Based_Methods_for_optimization_-_1/pasted_image003.png)
Average after 1 cycle - 493(improved)

*****

**Insights**:

* We have seen that 01100 will be discarded in the next cycle, because it's probability is the least
* This is not helpful because it is the only candidate with a one in the middle, any shuffling whatsoever will never result in the goal


**Remedy**:

* This can be taken care of if the initial population is bigger
* 



*****


* If the number of individuals in the starting population is large, then probability of a GA solution being good is high.


