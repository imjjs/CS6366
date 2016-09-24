Model
================================
:date: 2016-9-21 6:20
:modified: 2016-9-21 8:00
:tags: distributed AI
:category: cs6366
:slug: dai2
:authors: Yi Li
:summary: deliverable document 2


Basic
-----

- :math:`I = \{1, 2, ..., n\}`  is a collection of dynamic agents.

- :math:`G = (I, E)` is a time-invariant undirected connected graph describing neighborhood relations on :math:`I`, where :math:`E \subset I \times I` is the edge-set. By undirected we mean that :math:`\forall (i, j) \in E, (j, i) \in E`. The neighborhood of agent :math:`i` is denoted by :math:`N(i) = \{j\in I | (i,j) \in E\}`.

- :math:`S` is the state space and :math:`s^{(i)}_t \in S_i` denotes the state of agent :math:`i` at time :math:`t`, while :math:`\hat{s}_t \in S \subset \times_i S_i` is the state vector for all agents at time :math:`t`.

-  :math:`\mathcal{M} = (\Gamma, S, \hat{s}_0, A, P, g)` is a stochastic game, where :math:`A_i` is the action set of player :math:`i` and :math:`A = \times_i A_i`; :math:`P` is a transition probability from :math:`S \times A` to :math:`S`; A payoff function :math:`g: S \times A \rightarrow \mathbb{R}^I` whose i-th coordinate, :math:`g^{(i)}`, is a function of the state :math:`s^{(i)} \in S_i` and the action profile :math:`a^{(i)} \in A_i`.

- A play of stochastic game, :math:`\hat{s}_0 \hat{a}_0...\hat{s}_t\hat{a}_t...`, generates a sequence of payoff :math:`\hat{g}_0\hat{g}_1,...\hat{g}_t...`, where :math:`\hat{g}_t = g(\hat{s}_t, \hat{a}_t)`.

- A distributed and stationary control policy of i-th is denoted by a infinite sequence of control function, :math:`u^{(i)}_0u^{(i)}_1...u^{(i)}_t...`, where  :math:`u_t^{(i)}: S \rightarrow A_i`. By distributed we mean the agent makes decisions according the states of its neighbors ( :math:`u^{(i)}_t(\hat{s}) = u^{(i)}_t(\hat{s}')` if :math:`\forall j \in N(i)` and :math:`s^{(j)} = s'^{(j)}`).


Consensus
---------
- A consensus value is denoted by :math:`\mathcal{X}: S \rightarrow R`, which is permutation invariant: :math:`\mathcal{X}(s_1,s_2,...,s_n) = \mathcal{X}(s_{\sigma(1)}, s_{\sigma(2)},...,s_{\sigma(n)})`, where :math:`\sigma: I \rightarrow I`.

-  Agents reach asymptotically consensus on a consensus value if :math:`|| \hat{s}_t - \mathcal{X}(\hat{s_0})\cdot \hat{1}|| \rightarrow 0` for :math:`t \rightarrow \infty`.

- The comsensus problem: For a group of dynamic agents with neighborhood relations according to :math:`G(I,E)`. For any agreement function :math:`\mathcal{X}`, find a distributed and stationary protocol making agents reach asymptotically consensus on :math:`\mathcal{X(\hat{s}_0)}` for any initial state :math:`\hat{s}_0`.

Reachability
------------

- A path of i-th agent is a sequence of states denoted by, :math:`s_0^{(i)}s_1^{(i)}...s_t^{(i)}`, which can be generated under a control policy  by applying :math:`u^{(i)}_t(\hat{s}_t)` at state :math:`\hat{s}_t`.

- A collection of paths of i-th player under a control policy :math:`u` is denoted by :math:`Path^u_i = \{s_0^{(i)}s_1^{(i)}...s_t^{(i)}...| \forall t, P[s_{t+1}^{(i)}| s_t^{(i)}, a_t^{(i)} = u_t^{(i)}(\hat{s}_t)] > 0\}`.

- Obviously, :math:`Path` is a :math:`\sigma` algebra and we can define another probability measure :math:`P_{path}` on it. For example, the probability measure of a set of paths :math:`r^u` under policy :math:`u` having common prefix :math:`s_0^{(i)}s_1^{(i)}...s_t^{(i)}` can be defined as :math:`P_{path}(r^u) = \prod\limits_{i=1}^{t} P[s_{t+1}^{(i)}| s_t^{(i)}, u_t^{(i)}(\hat{s}_t)]` [2]_.

- One can shows a set of path under policy :math:`u` satisfying a LTL formula :math:`\phi` is measurable [1]_. We can define :math:`P_{path}[\{ r^u_i \in Path^u_i | r \vDash \phi \}]` as the probability of satisfying :math:`\phi` for player :math:`i` under policy :math:`u`.

- One can easily create an agreement function :math:`\mathcal{X}` based on the definition of :math:`P_{path}`, which means consensus values can be described by LTL logic.


.. [1] C. Baier, J.-P. Katoen, and K. G. Larsen, Principles of Model Checking. MIT Press, 2008.
.. [2] Ding, Xuchu Dennis, et al. "Optimal Control of Markov Decision Processes with Temporal Logic Constraints."
