# cartPoleEnv_hillClimbingAlgo


Features of Hill Climbing

1. Variant of generate and test algorithm: It is a variant of generating and test algorithm. The generate and test algorithm is as follows : 

1. Generate possible solutions. 
2. Test to see if this is the expected solution. 
3. If the solution has been found quit else go to step 1.

Hence we call Hill climbing a variant of generating and test algorithm as it takes the feedback from the test procedure. Then this feedback is utilized by the generator in deciding the next move in search space. 

2. Uses the Greedy approach: At any point in state space, the search moves in that direction only which optimizes the cost of function with the hope of finding the optimal solution at the end. 

Types of Hill Climbing 

Simple Hill climbing: It examines the neighboring nodes one by one and selects the first neighboring node which optimizes the current cost as the next node. 
Algorithm for Simple Hill climbing : 
 
    Step 1 : Evaluate the initial state. If it is a goal state then stop and return success. Otherwise, make initial state as current state. 

    Step 2 : Loop until the solution state is found or there are no new operators present which can be applied to the current state. 

a) Select a state that has not been yet applied to the current state and apply it to produce a new state. 

b) Perform these to evaluate new state 
    i. If the current state is a goal state, then stop and return success. 
    ii. If it is better than the current state, then make it current state and proceed further. 
    iii. If it is not better than the current state, then continue in the loop until a solution is found. 

Step 3 : Exit. 
 

2. Steepest-Ascent Hill climbing: It first examines all the neighboring nodes and then selects the node closest to the solution state as of the next node.            Algorithm for Simple Hill climbing :

       Step 1 :  Evaluate the initial state. If it is a goal state then stop and return success. Otherwise, make initial state as current state. 

       Step 2 : Repeat these steps until a solution is found or current state does not change 

a) Select a state that has not been yet applied to the current state.

b)  Initialize a new ‘best state’ equal to current state and apply it to produce a new state.

c) Perform these to evaluate new state                                                                                                                      i. If the current state is a goal state, then stop and return success.                                                                       ii. If it is better than best state, then make it best state else continue loop with another new state.

d) Make best state as current state and go to Step 2: b) part.

Step 3 : Exit

3. Stochastic hill climbing: It does not examine all the neighboring nodes before deciding which node to select. It just selects a neighboring node at random and decides (based on the amount of improvement in that          neighbor) whether to move to that neighbor or to examine another. 

       Step 1:  Evaluate the initial state. If it is a goal state then stop and return success. Otherwise, make the initial state the current state. 

       Step 2: Repeat these steps until a solution is found or the current state does not change.

       a) Select a state that has not been yet applied to the current state.

       b) Apply successor function to the current state and generate all the neighbor states.

       c) Among the generated neighbor states which are better than the current state choose a state randomly (or based on some probability function).                                                                                                                           

       d) If the chosen state is the goal state, then return success, else make it the current state and repeat step 2: b) part.

       Step 3: Exit.
State Space diagram for Hill Climbing

The state-space diagram is a graphical representation of the set of states our search algorithm can reach vs the value of our objective function(the function which we wish to maximize). 
X-axis: denotes the state space ie states or configuration our algorithm may reach. 
Y-axis: denotes the values of objective function corresponding to a particular state. 
The best solution will be that state space where the objective function has a maximum value(global maximum). 

![alt text](https://static.javatpoint.com/tutorial/ai/images/hill-climbing-algorithm-in-ai.png)


Different regions in the State Space Diagram: 

Local maximum: It is a state which is better than its neighboring state however there exists a state which is better than it(global maximum). This state is better because here the value of the objective function is higher than its neighbors. 
 
Global maximum: It is the best possible state in the state space diagram. This is because, at this stage, the objective function has the highest value.
Plateau/flat local maximum: It is a flat region of state space where neighboring states have the same value.
Ridge: It is a region that is higher than its neighbors but itself has a slope. It is a special kind of local maximum.
Current state: The region of state space diagram where we are currently present during the search.
Shoulder: It is a plateau that has an uphill edge.
Problems in different regions in Hill climbing

Hill climbing cannot reach the optimal/best state(global maximum) if it enters any of the following regions :  

Local maximum: At a local maximum all neighboring states have a value that is worse than the current state. Since hill-climbing uses a greedy approach, it will not move to the worse state and terminate itself. The process will end even though a better solution may exist. 
To overcome the local maximum problem: Utilize the backtracking technique. Maintain a list of visited states. If the search reaches an undesirable state, it can backtrack to the previous configuration and explore a new path.
Plateau: On the plateau, all neighbors have the same value. Hence, it is not possible to select the best direction. 
To overcome plateaus: Make a big jump. Randomly select a state far away from the current state. Chances are that we will land in a non-plateau region.

Ridge: Any point on a ridge can look like a peak because movement in all possible directions is downward. Hence the algorithm stops when it reaches this state. 
To overcome Ridge: In this kind of obstacle, use two or more rules before testing. It implies moving in several directions at once.




function HILL-CLIMBING(problem) returns a state that is a local maximum
 current ← problem.INITIAL-STATE
 loop do
   neighbor ← a highest-valued successor of current
   if VALUE(neighbour) ≤ VALUE(current) then return current
   current ← neighbor




function HILL-CLIMBING(problem) returns a state that is a local maximum
 current ← MAKE-NODE(problem.INITIAL-STATE)
 loop do
   neighbor ← a highest-valued successor of current
   if neighbor.VALUE ≤ current.VALUE then return current.STATE
   current ← neighbor



