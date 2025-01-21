$\text{min} \{ w(x) : x \in S \}$

$S$ = {insieme di archi che definiscono un cammino da un nodo sorgente ad un nodo pozzo t}

$x$ = variabile associata a un arco di G

$w(x):$ funzione che associa ad ogni soluzione il tempo di percorrenza

scritto in forma standard:

$$
\begin{array}{ll}
\text{min}  & \sum_{(u,v) \in A} \quad w_{(u,v) \ } \cdot x_{(u,v)}  \\\\
& ??? \\

& x \in \{0,1\}^{|A|}
\end{array}
$$
- $x_{(u,v)}$ assume valore $1$ quando l'arco $(u,v)$ viene considerato. 
- $w_{(u,v)}$ è il peso associato all' arco $(u,v)$.
Quali sono i vincoli che mancano? li vediamo tra poco.

Dati:
- grafo orientato e connesso $G(N,A)$
- esiste un cammino orientato da $s$ ad ogni $u \in N$
- due nodi speciali $s \in N$ e $t \in N - \{s\}$
- costi sugli archi  $w_{(u,v)} \quad \forall \ (u,v) \in A$

*Cosa stiamo cercando?*
L'obiettivo è trovare un cammino orientato  ottimo $P^*$ da $s$ a $t$ (avente costo minimo).
I cammini di interesse sono quindi cammini orientati $P$ dal nodo $s$ a $t$.

Per semplicità indichiamo il cammino P come un insieme di archi, quindi $A(P) = P$
Il costo di un cammino si scrive:
$$
w(P) = \sum_{(u,v) \in A(P)} w_{(u,v) \ }
$$

Due esempi di cammino e il loro costo:
- $P=\{sf, ft\} \qquad \qquad \quad \ w(P) = 8$
- $P’=\{sd,dc,cf,ft\} \qquad w(P’)=7$
## cammino ottimo

Definiamo il cammino ottimo $P^*$ come:
$$
P^* : w(P^*) \leq w(P) \quad \forall \ \text{cammino orientato \(P\) da \(s\) a \(t\) di } G(N,A) \quad
$$



Per indicare che i nostri archi del grafo hanno un verso introduciamo il concetto di vettore di incidenza.
Un vettore $x^P \in |0,1|^A$ è detto vettore di incidenza di un cammino P se è tale che
$$
\begin{cases}
x^P_{(u,v)} = 1 & (u,v) \in P  \\
\\
x^P_{(u,v)} = 0 & (u,v) \notin P  
\end{cases}
$$

Proprietà

- Da $s$ esce solo un arco di un cammino P
$$
\sum_{(u,s)x  \in {\delta^-_G}(s)} x^p_{(u,s)} = 0 \qquad \qquad \sum_{(s,u)x  \in {\delta^+_G}(s)} x^p_{(s,u)} = 1
$$

- in $t$ entra solo un arco di $P$
$$
\sum_{(u,t)x  \in {\delta^-_G}(t)} x^p_{(u,t)} = 1 \qquad \qquad \sum_{(u,t)x  \in {\delta^+_G}(t)} x^p_{(u,t)} = 0
$$

- In ogni altro nodo $v \in (s,t)$ il numero di archi di $P$ entranti è uguale al numero di archi di $P$ uscenti
$$
\sum_{(u,v)x  \in {\delta^-_G}(v)} x^p_{(u,v)} = \sum_{(v,u)x  \in {\delta^+_G}(v)} x^p_{(v,u)}
$$

Il problema di cammino minimo può quindi essere scritto:

$$
\begin{array}{ll}

\text{min} & \sum_{(u,v) \in A} \ w_{(u,v)  } \cdot x_{(u,v)}  \\\\
st & \sum_{(u,s)x  \in {\delta^-_G}(s)} x^p_{(u,s)} = 0 \\
& \sum_{(s,u)x  \in {\delta^+_G}(s)} x^p_{(s,u)} = 1 \\
& \sum_{(u,v)x  \in {\delta^-_G}(v)} x^p_{(u,v)} - 
\sum_{(v,u)x  \in {\delta^+_G}(v)} x^p_{(v,u)} = 0 \\
& \sum_{(u,t)x  \in {\delta^+_G}(t)} x^p_{(u,t)} = 0 \\
& \sum_{(u,t)x  \in {\delta^-_G}(t)} x^p_{(u,t)} = 1 \\
& x \in \{0,1\}^{|A|}
 
\end{array}
$$

o anche:

$$
\begin{array}{ll}

\text{min} & \sum_{(u,v) \in A} \ w_{(u,v)  } \cdot x_{(u,v)}  \\\\
st & Mx = d \\
& x \in \{0,1\}^{|A|}
\end{array}
$$


Cammino Minimo come Problema di Flusso Intero

Dati:
- Un grafo orientato $G(N,A)$
- Un vettore capacità $c = \infty_{|A|}$  
- un vettore costi $w \in R^{|a|}$
- un vettore domanda $d_{(s,t)} = (s,\ ...,\ t)^T$

$$
\begin{array}{ll}

\text{min} & \sum_{(i,j) \in A} \ w_{(i,j)  } \cdot x_{(i,j)}  \\\\
st
& \sum_{(j,i)x  \in {\delta^-_G}(i)} x^p_{(j,i)} - 
\sum_{(i,j)x  \in {\delta^+_G}(i)} x^p_{(i,k)} = d_i & \forall \ i \in N\\
& \sum_{(u,t)x  \in {\delta^+_G}(t)} x^p_{(u,t)} = 0 \\
& \sum_{(u,t)x  \in {\delta^-_G}(t)} x^p_{(u,t)} = 1 \\
& x_{(i,j)} \geq 0 &\forall (i,j) \in A

\end{array}
$$



