
$$\text{min} \ \{f(x): x \in S\}$$

variabile decisionale:
$x = \text{variabile associata ad ogni nodo del grafo G}$

soluzione ammissibile:
$S = \{\text{nodi incidenti con ogni arco del grafo G almeno una volta}\}$

funzione obiettivo:
$f(x): \text{funzione che associa a ogni nodo del grafo G un costo pari a 1}$


$x$ non è un singolo valore, ma piuttosto un insieme di variabili associate a ciascun nodo del grafo $G$
Tipicamente se $G = (N, A)$ ha insiemi di vertici $N = \{v_1,v_2,...,v_n\}$, definiamo variabili binarie $x_i$ per ogni $v_i \in N$ dove:
$$
x_i = \begin{cases}
1 & \text{se il nodo \(v_i\) è scelto nella copertura,}  \\
0 & \text{altrimenti}
\end{cases}
$$
In alternativa si può intendere $x$ come un vettore $(x_1,x_2,...,x_n)$

Quindi potrebbe essere $x = (1,0,0,1,1)$

Un'assegnazione $x$ è ammissibile se per ogni arco $(u,v) \in N$ almeno uno dei suoi nodi è incluso nella copertura, cioè $x_u = 1$ oppure $x_v = 1$.
Quindi $S$ rappresenta l'insieme di tutti i possibili vettori $x$ tali che ogni arco è "coperto" da almeno un estremo.

Formalmente:

$$ S  = \{x \in \{0,1\}^n \mid  \forall (u,v) \in N , \ x_u + x_v \geq 1 \}. $$


Problema di node-cover di peso minimo

$$
\begin{array}{ll}
\text{min}  & \sum_{v \in N} \ x_v  \\
\text{s t} & x_u + x_v \geq 1 && \forall\ (u,v) \in A  \\
& x \in \{0,1\}^{|N|}
\end{array}
$$


Problema di insieme stabile di peso massimo

$$
\begin{array}{ll}
\text{min}  & \sum_{v \in N} \ x_v  \\
\text{s t} & x_u + x_v \leq 1 && \forall\ (u,v) \in A  \\
& x \in \{0,1\}^{|N|}
\end{array}
$$


Problema di matching di peso massimo

$$
\begin{array}{ll}
\text{min}  & \sum_{uv \in A} \ x_{uv}  \\
\text{s t} & \sum_{u \in N_G (v)} x_{uv} \leq 1 && \forall\ v \in N  \\
& x \in \{0,1\}^{|A|}
\end{array}
$$

