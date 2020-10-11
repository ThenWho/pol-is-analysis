Pol.is Graph Theoretic Modeling

Formalizing the Pol.is graph

|  |
| :--- |
| We use the following process to improve this doc :
|1. If you're reading this, you're welcome to contribute! 🎉
|2. Work in suggestion mode.
|3. Make use of comments and ample +1s.
|4. Each section has a steward (in parenthesis).
|5. Accept/reject comments of the sections that you are steward of.
|6. To start working in a new direction:
|a. start a new section and
|b. put yourself as a steward. |

Document Steward: Giorgos Georgiadis (GG)

LaTeX equations plugin: [https://gsuite.google.com/marketplace/app/autolatex_equations/850293439076](https://www.google.com/url?q=https://gsuite.google.com/marketplace/app/autolatex_equations/850293439076&sa=D&ust=1602440807647000&usg=AOvVaw3a2VniQvbuqJoCEFamEXTM)

# Introduction (GG)

Pol.is[[1]](#ftnt1) is a deliberation platform where participants are called to vote (agree/disagree/pass) on a number of statements. At the same time, they are free to add their own statements for subsequent users to vote on<sup>[[2]](#ftnt2)</sup>.

This document aims to study the resulting poll from a graph theoretical point of view, and derive, if possible, useful analytical properties. Possible uses for this analysis are

* strengthening the polling process (e.g. resistance to coordinated voting attacks),
* suggesting directions of improvement,
* better understanding of the computational complexity of common actions,
* ...

***

# Modeling (GG)

## Definitions

Let ${G_t} = ({U_t},{V_t},{E_t})$ be a bipartite graph<sup>[[3]](#ftnt3)</sup> representing a poll at time $t$. For every user $u$ that has participated in the poll by time $t$, there is a node $u \in U_t$. Respectively, for every statement $v$ that is part of the poll by time $t$, there is a node $v \in V_t$. If a user $u$ has voted on some statement $v$, then an edge $(u,v) \in {E_t}$ exists. We distinguish between three types of edges: those belonging to positive ("agree"), negative("disagree") and neutral ("pass") votes, represented with $E_t^ + ,E_t^ - ,E_t^0$ respectively ($E_t^ +  \cup E_t^ -  \cup E_t^0 = {E_t}$). When a user votes for a statement, an appropriate edge is being created, depending on the type of the vote (positive, negative or neutral).

We treat this graph as a multiplex network<sup>[[4]](#ftnt4)</sup> with three layers , where the layers are being defined by the three types of edges (edges of a type reside all in the same layer), all nodes are common among all layers, and there are no interlayers edges. We will be using the formal notation of multiplex networks only when strictly necessary. To simplify further, the edge sets $E_t^ + ,E_t^ - ,E_t^0$ will be used to represent the layers they belong to, where it is clear from context that we refer to the one or the other.

## Graph generation model

We assume discrete time and that no two users arrive simultaneously at the poll, i.e. one user arrives at time $t$ and the other at time ${t^{'}}$, such that $t < {t^{'}}$.

At time $t = 0$, we have $\left| {{U_0}} \right| = 0,\left| {{V_0}} \right| = n_0^v,\left| {{E_0}} \right| = 0$. This reflects the fact that the poll starts with no users, a set of initial statements and no votes.

At time $t-1$, we consider the graph ${G_{t-1}} = ({U_{t-1}},{V_{t-1}},{E_{t-1}})$ as described in the previous section.

At each time $t$, either a new user ${u_t} \notin {U_{t - 1}}$ participates in the poll (such that ${u_t} \cup {U_{t - 1}} = {U_t}$) or an existing user $u \in {U_{t - 1}}$ returns.

* A new user ${u_t}$ votes for $0$ or $k \geq 1$ existing statements $v_t^1, \ldots ,v_t^k \in V_{t-1}$. Voting creates the corresponding edges, ${({u_t},v_t^1), \ldots ,({u_t},v_t^k)}$, such that ${E_{t - 1}} \cup \left\{ {({u_t},v_t^1), \ldots ,({u_t},v_t^k)} \right\} = {E_t}$, or no edges in case of no voting (implying ${E_{t - 1}} = {E_t}$). User ${u_t}$ can also create $0$ or $l \ge 1$ new statements $v_t^1, \ldots ,v_t^l \notin {V_{t - 1}}$, such that ${V_{t - 1}} \cup \left\{ {v_t^1, \ldots ,v_t^l} \right\} = {V_t}$ (if no statements are created, ${V_{t - 1}} = {V_t}$).
* An existing, returning user $u$ visited the poll latest at time $t^{'} < t$, either as a new user or returning one (i.e. an existing user may return multiple times). On time $t$ they vote for $0$ or $k \geq 1$ existing statements $v_t^1, \ldots ,v_t^k \in V_{({t^{'}},t)}$, where ${V_{({t^{'}},{t-1})}}$ is the set of all statements added to the poll between time ${t^{'}}$ and $t-1$ (possibly $\emptyset $ if ${t^{'}} = t - 1$). Similarly to the previous case, user ${u}$ can also create $0$ or $l \ge 1$ new statements $v_t^1, \ldots ,v_t^l \notin {V_{t - 1}}$, such that ${V_{t - 1}} \cup \left\{ {v_t^1, \ldots ,v_t^l} \right\} = {V_t}$ (if no statements are created, ${V_{t - 1}} = {V_t}$).

# TODO / interesting directions

* [https://iopscience.iop.org/article/10.1088/1367-2630/ab14b3](https://www.google.com/url?q=https://iopscience.iop.org/article/10.1088/1367-2630/ab14b3&sa=D&ust=1602440807651000&usg=AOvVaw3Bfq4iZGEATn3g4gaBajI-)

* Here the authors suggest that

1. if you use any type of centrality measure in each network layer (e.g. degree centrality for the positive-answers layer and 'inverse degree' centrality for the negative-answers) but convert it into 'rank'...
2. ... you can work in a unifying way over all layers and eg define a sort of distance  between them.

In the polis' case, this could mean distance from an ideal unanimous consensus (everybody agrees on all statements). This isn't interesting (or realistic) as an absolute value but could be used to find statements that can make a big difference if they are improved (ie they decrease distance from 'unanimous consensus' more than others).

* [https://arxiv.org/abs/1501.06444](https://www.google.com/url?q=https://arxiv.org/abs/1501.06444&sa=D&ust=1602440807651000&usg=AOvVaw2Cl-kUEmsm97k4-nMFiydY)

* Stochastic block models for multiple networks  can give you the probability that a given node belongs to a given cluster/block over all 3 layers (agree/pass/disagree), without squishing the different relationships into one.

***

[[1]](#ftnt-ref1) [https://pol.is/](https://www.google.com/url?q=https://pol.is/&sa=D&ust=1602440807653000&usg=AOvVaw3h99UEMlmU0ndFt28GqDMu)

[[2]](#ftnt-ref2) [https://roamresearch.com/#/app/polis-methods/page/1GR4r4LX8](https://www.google.com/url?q=https://roamresearch.com/%23/app/polis-methods/page/1GR4r4LX8&sa=D&ust=1602440807652000&usg=AOvVaw3nfUTwVC-d5GcA_zrPZ2jA)

[[3]](#ftnt-ref3) [https://en.wikipedia.org/wiki/Bipartite_graph](https://www.google.com/url?q=https://en.wikipedia.org/wiki/Bipartite_graph&sa=D&ust=1602440807652000&usg=AOvVaw340Mib1ttSuqd-P2dKHnNo)

[[4]](#ftnt-ref4)Cozzo, E., De Arruda, G. F., Rodrigues, F. A., & Moreno, Y. (2018). Multiplex networks: basic formalism and structural properties . Berlin: Springer.
