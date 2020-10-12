## Graph generation model

We assume discrete time and that no two users arrive simultaneously at the poll, i.e. one user arrives at time $t$ and the other at time ${t^{'}}$, such that $t < {t^{'}}$.

At time $t = 0$, we have $\left| {{U_0}} \right| = 0,\left| {{V_0}} \right| = n_0^v,\left| {{E_0}} \right| = 0$. This reflects the fact that the poll starts with no users, a set of initial statements and no votes.

At time $t-1$, we consider the graph ${G_{t-1}} = ({U_{t-1}},{V_{t-1}},{E_{t-1}})$ as described in the previous section.

At each time $t$, either a new user ${u_t} \notin {U_{t - 1}}$ participates in the poll (such that ${u_t} \cup {U_{t - 1}} = {U_t}$) or an existing user $u \in {U_{t - 1}}$ returns.

* A new user ${u_t}$ votes for $0$ or $k \geq 1$ existing statements $v_t^1, \ldots ,v_t^k \in V_{t-1}$. Voting creates the corresponding edges, ${({u_t},v_t^1), \ldots ,({u_t},v_t^k)}$, such that ${E_{t - 1}} \cup \left\{ {({u_t},v_t^1), \ldots ,({u_t},v_t^k)} \right\} = {E_t}$, or no edges in case of no voting (implying ${E_{t - 1}} = {E_t}$). User ${u_t}$ can also create $0$ or $l \ge 1$ new statements $v_t^1, \ldots ,v_t^l \notin {V_{t - 1}}$, such that ${V_{t - 1}} \cup \left\{ {v_t^1, \ldots ,v_t^l} \right\} = {V_t}$ (if no statements are created, ${V_{t - 1}} = {V_t}$).
* An existing, returning user $u$ visited the poll latest at time $t^{'} < t$, either as a new user or returning one (i.e. an existing user may return multiple times). On time $t$ they vote for $0$ or $k \geq 1$ existing statements $v_t^1, \ldots ,v_t^k \in V_{({t^{'}},t)}$, where ${V_{({t^{'}},{t-1})}}$ is the set of all statements added to the poll between time ${t^{'}}$ and $t-1$ (possibly $\emptyset $ if ${t^{'}} = t - 1$). Similarly to the previous case, user ${u}$ can also create $0$ or $l \ge 1$ new statements $v_t^1, \ldots ,v_t^l \notin {V_{t - 1}}$, such that ${V_{t - 1}} \cup \left\{ {v_t^1, \ldots ,v_t^l} \right\} = {V_t}$ (if no statements are created, ${V_{t - 1}} = {V_t}$).