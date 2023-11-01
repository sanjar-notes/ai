# 1. L6 - State Space Search
Created Monday 05 October 2020


* This aspect of AI is called problem solving.
* We want to change our situation(Start → Goal), using a series of steps. We represent the situations as a state space.
* Other aspects of AI include knowledge based systems, rule based systems etc. Expert systems require some information on which the recommendations were based.
* Search based techniques are not devoid of knowledge, as we still have to model the search space appropriately.


*****


* Search based methods are called first principle methods.
* Pure search based approach is not suitable, because it suffers from something called combinatorial explosion.
* We use heuristics to guide the search, and avoid combinatorial explosion.


*****

Puzzles:

1. Rubic cube 3x3
2. n^2 ^- 1 puzzle

![](./1._L6_-_State_Space_Search/pasted_image.png)

3. Man, Goat, Lion and cabbage problem.
4. Cups of some size. Pour liquid of some volume from a reservoir.


*****

State Space Search - details:

1. State representation(it should be non-redundant and easy to write algorithms for)
2. *MoveGen*(**state**) - generates all neigbouring states from the given **state**.
3. GoatTest(**state**) - checks if **state** is the goal. In some problems we need to match certain constraints for the goal state, i.e the goal state is not explicitly defined, e.g N-queens problem


* **S** - start state, **G** - Goal state
* **OPEN** - the set of unexplored states. Short for - *open* to exploration. This is just our current search space. It is obviously necessary.
* **CLOSED** - the set of explored nodes. Short for - *closed* for exploration. This is necessary, to avoid the problem of an infinite loop. Just consider the previous move, the shortest cycle. Previous ↔ Current. More sophisticated cycles are also possible.
* This approach is also called generate and test.
* This approach is domain independent.


*****

Notation:

1. Double circles - node has been explored

![](./1._L6_-_State_Space_Search/pasted_image001.png)


*****

**Simple Search 1**
	OPEN = {S}
	N = S // current state
	while GoalTest(N)!=True:
		Remove N from OPEN
		OPEN = OPEN U MoveGen(N) /* U for union */
		N = select_state_from_OPEN() /* returns NULL if OPEN is empty*/

Problems with this algo:

1. Infinite loops due to cycles are possible - algo is thus invalid

Soln: CLOSED set

2. What if OPEN becomes empty - i.e we explore all nodes - while loop never stops

Soln: Check if OPEN is non-empty

* Note: We are randdomly selecting N at each step, this could be improved.


*****

**Simple Search 2**
	OPEN = {S}
	CLOSED = {}
	N = S // current state
	while GoalTest(N)!=True && N==null:
		Remove N from OPEN
		CLOSED = CLOSED U N /* U for union */
		OPEN = OPEN U MoveGen(N)
		N = select_state_from_OPEN() /* returns NULL if OEEN is empty*/

Problems with this algo:

1. Our algo only checks whether a solution exists, not how to reach it. i.e it does not generate the steps.


