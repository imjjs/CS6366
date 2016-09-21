Basic Model
================================
:date: 2016-9-21 6:20
:modified: 2016-9-21 8:00
:tags: distributed AI
:category: cs6366
:slug: dai2
:authors: Yi Li
:summary: project proposal



Definition
----------
- :math:`\Gamma = \{\gamma_1, \gamma_2, ..., \gamma_n\}`  is a collection of dynamic agents and :math:`\gamma_i` is the i-th agent.

- :math:`G = (\Gamma, E)` is a time-invariant undirected connected graph describing neighborhood relations on :math:`\Gamma`, where :math:`E \subset \Gamma \times \Gamma` is the edge-set. By undirected we mean that :math:`\forall (\gamma_i, \gamma_j) \in E, (\gamma_j, \gamma_i) \in E`. The neighborhood of :math:`\gamma_i` is denoted by :math:`N(\gamma_i) = \{\gamma_j\in \Gamma : (\gamma_i,\gamma_j) \in E\}`.

- :math:`S` is the state space and :math:`s_t(\gamma_i) \in S` denotes the state of agent :math:`\gamma_i` at time :math:`t`, while :math:`\vec{s_t} = (s_t(\gamma_1), s_t(\gamma_2),..., s_t(\gamma_n)) \in S^n` is the state vector for all agents at time :math:`t`.

- A distributed and stationary control policy of i-th agent at time :math:`t` is denoted by :math:`u^{(i)}_t: S^n \rightarrow A`, where $A$ is the action set. By distributed we mean the agent makes decisions according the states of its neighbors ( :math:`u^{(i)}_t(\vec{s_t}) = u^{(i)}_t(\vec{s'_t})` if :math:`\forall j, \gamma_j \in N(\gamma_i)` and :math:`s_t(\gamma_j) = s'_t(\gamma_j)`)
