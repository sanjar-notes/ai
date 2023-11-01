# 3. L11 - Beam Search
Created Saturday 10 October 2020

B-SAT problem - given a boolean expression, find the values of the variables such that the expression evaluates to true.
Some notations, jargon:

1. Clause - atomic expression
2. Literal - number of variables in a clause


* 2-SAT is solvable using David Putnam method. 3-SAT and higher are NP-complete
* For n variables, there are 2^n^ states.
* This is clearly exponential.



*****

**Beam Search**
This is a very simple change to the Hill climbing algorithm. Instead of selecting one best succesor, we select best 'k' successors, i.e beam length is k.
Properties:

* Space: Linear, O(k+b) - k is beam size
* Time: Linear, uses a heuristic and best ones.
* Completness - incomplete, may get stuck at a local maxima
* Quality - NA(incomplete)



*****

Importance of Beam Search:

* When multiple options may be correct, we select multiple options and go ahead.
* The number of options kept alive are constant(k=beam length)
* Beam search avoids the problem of local extrema.

Beam Seach Pseudocode:
	def Beam_Search(S, moveGen, h, bw):
		BEAM = [S, null]
		while BEAM.length==bw:
			for node in BEAM:
				if goalTest(node)==true:
					return node
			newBeam = []
			for node in BEAM:
				newBeam = merge(newBeam, sort(moveGen(node)))[n-bw:]
			BEAM = newBeam
		return null



*****

Applications of Beam Search:

* Speech recognition
* Signal processing - Viterbi algorithm



*****

**Solution Space Search**
Instead of constructing the state variable wise, we start with a solution(a binary array in SAT problems). We proceed by perturbating the state to different states, by some slight change. The perturbation is carried out by the moveGen function. 

* This is not different from state space search.

![](./3._L11_-_Beam_Search/pasted_image.png)

* In the solutions space search, it is better if we have a denser moveGen function, because the probability of a state being a local maxima is less if the density is higher(more states are lower than the given state).
* A sparse movbeGen function has the problem of local extrema, wihe a very dense moveGen function is also useless, as it increases the time complexity, making the heuristic search tend to a brute-force approach.



*****

**Variable Neighbourhood Decomposition**
The  neighbour hood function is not fixed, it changes over time. 
![](./3._L11_-_Beam_Search/pasted_image001.png)

*****

e.g for a rubiks cube champion, he/she will disrupt the cube at times to and slowly stablize it. y-axis represents the pieces out of place.
![](./3._L11_-_Beam_Search/pasted_image002.png)

* In the real world, it is very difficult to find heuristic search algorithms which have a smooth surface.
* There are two kinds of moves in any heuristic search:
	1. Exploitation - following the heuristic function
	2. Exploration - disobeying the heuristic function


