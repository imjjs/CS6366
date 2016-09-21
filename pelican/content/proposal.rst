Consensus in Multi-Agent System
================================
:date: 2016-9-08 10:20
:modified: 2016-9-20 14:00
:tags: distributed AI
:category: cs6366
:slug: dai1
:authors: Yi Li
:summary: project proposal



Motivation
----------
Due to broad applications of multi-agent systems in many fields including cooperative control of UAVs, flocking, distributed sensor networks and congestion control in communication networks, distributed coordination of network of dynamic agents have been studied extensively in the literature. In many application related to multi-agent systems, agents groups need to reach consensus, that is to converge to a same value which might or might not be related to the motion of the individual agents. This kind of problems called consensus problems. Although the consensus problem has a long history in the field of computer science, in particular automaton theory and distributed computation, it becomes an important issue that need to be addressed in distributed artificial intelligence.

Description
-----------
The project is about studying consensus in multi-agent systems. The core idea is that the consensus problem can be turned into a non-cooperative stochastic game, where the dynamic agents are players. The consensus can be formally represented by a mechanism design problem including the objective functions such that if the rational agents use their best-response strategies, then such objective functions lead the whole system to a consensus value. Moreover, we assume that neighborhood relations are defined in the players set and each player has a optimal, distributed, and stationary control policy making decisions based on its neighbors’ states.

Several optional topics may be included in this project:
    - Make a comparison between our model and traditional approaches for solving consensus problems.
    - Find the connections between consensus problems and formal verifications (currently, my idea is if the consensus value or agreement functions can be represented by LTL formulas ).
    - Do equilibrium approximate computations for large scale stochastic games.

Evaluation
----------
I am considering several options (this part might be changed if there is a better idea coming).

- Optimal power flow problems. Using PyPower creates and simulates a decentralized power grid. The agents includes power generators and consumers and the neighborhood relations can be defined by the topological structure of power grids. The behaviors of whole system can be treated as a MDP. Some properties, like avoiding power overload, can be considered as the consensus. Finally, we measure the tendency of the whole system. (does the agents converge to the consensus with their optimal control policies ?)

- Retailers inventory control. Idea is similar to optimal power flow problems. Using matlab as the simulator.

Schedule
--------
- Sept. 22nd: finish formal definition of the problem model.
- Oct. 11th: define and get the primary solutions of the consensus problem.
- Oct. 27th: refine the solutions of the consensus problem and solve the mechanism design.
- Nov. 15th: implement the experiments.
- Nov. 29th: deliver the project.
- Project Website: https://my.vanderbilt.edu/liyi/homepage/distributed-ai-project/

Reference
---------
[1] Bauso, Dario, Laura Giarré, and Raffaele Pesenti. "Non-linear protocols for optimal distributed consensus in networks of dynamic agents." Systems & Control Letters 55.11 (2006): 918-928.

[2] Ren, Wei, Randal W. Beard, and Ella M. Atkins. "A survey of consensus problems in multi-agent coordination." Proceedings of the 2005, American Control Conference, 2005.. IEEE, 2005.

[3]Sarimveis, Haralambos, et al. "Dynamic modeling and control of supply chain systems: A review." Computers & Operations Research 35.11 (2008): 3530-3561.

[4] Fred S. Roberts, "Computer science and decision theory", Annals of Operations Research, 2008.
