Deliverable 3
================================
:date: 2016-10-11 6:20
:modified: 2016-10-11 8:00
:tags: distributed AI
:category: cs6366
:slug: dai3
:authors: Yi Li
:summary: deliverable 3

**Document can be download from** https://imjjs.github.io/cs6366/d3.pdf

**I pledge my honor that I have neither given nor received aid on this work.**

Progress
--------------------------------
In deliverable 2, the basic model for generic consensus problems has been defined. In this time, I defined the mechanism design problem and narrow down the model by considering a specific application.

Refinement for the generic model
++++++++++++++++++++++++++++++++

Let's introduce a generic cost function for i-th agent: :math:`J_i(x_i, N(x_i), a_i) = \lim\limits_{T \rightarrow \infty} \sum \limits_{i=0}^T F(x_i, N(x_i), a_i)`, where :math:`F` is a nonnegative penalty function accounting for the deviation of player i from its neighbors.

We say that a protocol is optimal, if each control :math:`a_i` minimizes :math:`J_i`. Recall we have the definition of consensus problem in deliverable 2. We say that a protocol is a consensus protocol if it is solution of the consensus problem. Furthermore, a consensus protocol is said to be optimal, if the controls :math:`a_i` minimize :math:`J_i`.

Thus, the mechanism design problem can be defined as: For any agreement function :math:`\mathcal{X}` design a penalty function :math:`F` such that there exists an optimal consensus protocol :math:`a` with respect to :math:`\mathcal{X}(\hat{s}_0)` for any initial state :math:`\hat{s}(0)`.


Application: Target tracking with distributed sensors
+++++++++++++++++++++++++++++++++++++++++++++++++++++

description
___________
In this problem, there are multiple probes which can freely move around in a bounded space, and a target which is unobservable for all the probes. At any time, a probe can emit pulses of sounds and get a noisy distance to the target. The noise level is in direct proportion to the distance between the probe and the target, which means the more a probe is close to the target, the more accurate results the probe can get. Each probe has limited communication range and can only share its position and observations with their neighbors. The goal of this problem is trying to locate the position of the invisible target.

model
_____

The basic framework is defined according to the generic model in deliverable 2. Several extended assumptions are described below:

- Each probe is a player.
- Probes move around in a bounded 2d euclidean plane so that the state space are the possible combinations of the positions and velocities of all the probes.
- The actions of a probe are represented by the vectors of acceleration.
- At each stage, a probe chooses an action (its current acceleration) and moves to the position at the next stage. Assume the actual moving distance equals to the theoretical moving distance plus a random variable with Gaussian distribution.
- At each stage, a probe can get an observation including the distance to the target and the signal strength. The observed distance equals to the actual distance plus a random variable with Gaussian distribution. The value of :math:`\sigma` is in direct proportion to the actual distance.
- The goal of the game is that probes try to locate the target.

By considering the discrete time model, a stochastic game can be defined for representing this problem.

Schedule
--------
In this time, I added a specific application model instead of directly solving the consensus problem. Because both mechanism design problem and consensus problem can be solved more easily under concrete definitions and the questions in the discussion section of this assignment cannot be answered without an application. For the next assignment, I will illustrate the solutions for both problems and start to implement the simulation program. A demo will be available before the project demonstration.

Discussion
----------
(a)
For each probe in the tracking problem,

- It can know the positions and velocities of its neighbors and itself.
- It can know the observations from its neighbors.
- It can estimate the consequences of its actions (the position of itself at the next stage with noise)
- It can estimate the distance to the target.
- It believes that the communications between itself and its neighbors are reliable and its neighbors cannot deceive it.
- It believes that the observations from its neighbors are inaccurate.
- It believes that it moves around in the euclidean plane.

(b)
The knowledge of movement and the states of neighborhood is included in the framework of games. The knowledge of observations is integrated into the cost function. The neighborhood relations are defined by the distance on the euclidean plane. The uncertainty in the knowledge of movement makes the game model be a stochastic game.

(c)
The uncertainty is represented by the random variable with Gaussian distribution. It works for the model, although it usually is a strong assumption in the real world.

Since the knowledge of states of probes is a kinematics issues, it can be represented by the Cartesian coordinate system and classic Newton's laws. Such representation works under the assumptions of the application model, but may not work in the real world. For example, tracking a target over the surface of ocean is not a system on the euclidean plane, and finding the trace of a high-energy particle in LHC is not a system under classic Newton's laws.


Reference
---------
[1] Bauso, Dario, Laura Giarré, and Raffaele Pesenti. "Non-linear protocols for optimal distributed consensus in networks of dynamic agents." Systems & Control Letters 55.11 (2006): 918-928.

[2] Ren, Wei, Randal W. Beard, and Ella M. Atkins. "A survey of consensus problems in multi-agent coordination." Proceedings of the 2005, American Control Conference, 2005.. IEEE, 2005.

[3]Sarimveis, Haralambos, et al. "Dynamic modeling and control of supply chain systems: A review." Computers & Operations Research 35.11 (2008): 3530-3561.
