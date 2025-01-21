

Definizione problema di flusso a costo minimo

Le componenti sono: 
- Un grafo orientato $G(N,A)$
- Una domanda $d_i$ associata ad ogni nodo $i \in N$ (la domanda può assumere valori negativi se invece di ricevere fornisce, nulla se è un nodo di transito)
- Un costo $w_j$ associato ad ogni arco $(i,j) \in A$
- Una capacità $c_{(i,j)}$ associata ad ogni arco $(i,j) \in A$ , che rappresentà la massima quantità che può passare in un arco

L'obiettivo è trovare un flusso $x_{(i,j)}$ sul grafo $(G,c,d)$ da inviare su ogni arco $(i,j) \in A$ tale che il costo totale $w^T x$ sia minimizzato ( e le richieste di capacità rispettate ).

Il flusso $x \in R^{|A|}$ deve rispettare due condizioni:

1.  La differenza tra il flusso entrante ed il flusso uscente deve essere uguale alla domanda. Sommando su tutti i nodi, la somma delle domande deve essere nulla: $$ \sum_{j \in N^-(i)} x_{(j,i)} \ - \ \sum_{k \in N^+(i)} x_{(i,k)} = d_i \qquad \forall \ i \in N $$ 
2.  Il flusso deve essere non-negativo e non deve essere superiore alla capacità: $$ 0 \leq x_{(i,j)} \leq c_{(i,j)} \qquad \forall \ (i,j) \in A $$

Problema di flusso a costo minimo MCF
$$
\begin{array}{ll}
\text{min}  & \sum_{(i,j) \in A} \ w_{(i,j)} \ x_{(i,j)}  \\ \\
\text{s t} & \sum_{j \in N^-(i)} x_{(j,i)} \ - \ \sum_{k \in N^+(i)} x_{(i,k)} = d_i & \forall \ i \in N  \\
& 0 \leq x_{(i,j)} \leq c_{(i,j)} & \forall \ (i,j) \in A
\end{array}
$$

Il problema può essere semplificato introducendo la matrice di incidenza

