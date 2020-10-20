---
title Pol.is Analysis / Definitions
description Definitions
---
# Definitions

Let ${G_t} = ({U_t},{V_t},{E_t})$ be a bipartite graph<sup>[[2]](#ftnt2)</sup> representing a poll at time $t$. For every user $u$ that has participated in the poll by time $t$, there is a node $u \in U_t$. Respectively, for every statement $v$ that is part of the poll by time $t$, there is a node $v \in V_t$. If a user $u$ has voted on some statement $v$, then an edge $(u,v) \in {E_t}$ exists. We distinguish between three types of edges: those belonging to positive ("agree"), negative("disagree") and neutral ("pass") votes, represented with $E_t^ + ,E_t^ - ,E_t^0$ respectively ($E_t^ +  \cup E_t^ -  \cup E_t^0 = {E_t}$). When a user votes for a statement, an appropriate edge is being created, depending on the type of the vote (positive, negative or neutral).

![](https://i.imgur.com/Al3kqn5.png =500x)

We treat this graph as a multiplex network<sup>[[3]](#ftnt3)</sup> with three layers , where the layers are being defined by the three types of edges (edges of a type reside all in the same layer), all nodes are common among all layers, and there are no interlayers edges. We will be using the formal notation of multiplex networks only when strictly necessary. To simplify further, the edge sets $E_t^ + ,E_t^ - ,E_t^0$ will be used to represent the layers they belong to, where it is clear from context that we refer to the one or the other.

![](https://i.imgur.com/swvvAWw.png =500x)


[[2]](#ftnt-ref2) [https://en.wikipedia.org/wiki/Bipartite_graph](https://en.wikipedia.org/wiki/Bipartite_graph)

[[3]](#ftnt-ref3)Cozzo, E., De Arruda, G. F., Rodrigues, F. A., & Moreno, Y. (2018). Multiplex networks: basic formalism and structural properties . Berlin: Springer.

[> home](https://hackmd.io/@ThenWho/PolisGraph)