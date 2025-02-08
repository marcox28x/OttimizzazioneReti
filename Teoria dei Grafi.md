GRAFO COMPLETO
Un grafo completo è un grafo tale che ogni nodo è collegato ad ogni altro.

GRAFO VUOTO
Un grafo vuoto è un grafo senza archi.

GRAFO COMPLEMENTO (o INVERSO) di $G(N,A)$
Un grafo complemento $\overline{G}(V,E)$ di un grafo $G(N,A)$ è un grafo con gli stessi nodi di $G(N,A)$ per cui esiste un arco per ogni coppia di nodi non adiacente in $G(N,A)$.


STELLA DI $v$ IN $G$
Insieme degli archi di $G$ incidenti su $v$:
$$\delta_G(v) = \{e \ : \ e = uv\} \subseteq A$$

GRADO DI $v$ IN $G$
Cardinalità della stella di $v$ in $G$
$$d_G (v) = |\delta_G(v)|$$

INTORNO DI $v$ IN $G$
Insieme dei nodi adiacenti a $v$ in $G$
$$N_G(v) = \{ u \ : \ vu \in A \} \subseteq N$$

STELLA USCENTE DA v IN G
Insieme degli archi di $G$ uscenti da $v$
$$\delta^+_G(v) = \{ e : v \ \text{coda di } e \} \subseteq A$$
$$d^+_G (v) = |\delta^+_G (v)| \quad \text{grado uscente}$$
 

STELLA ENTRANTE IN v IN G
Insieme degli archi di $G$ entranti da $v$
$$\delta^-_G(v) = \{ e : v \ \text{testa di } e \} \subseteq A$$
$$d^-_G (v) = |\delta^-_G (v)| \quad \text{grado entrante}$$

INTORNO USCENTE DI $v$ IN $G$


INTORNO ENTRANTE DI v IN G



# Walk
Un walk è una sequenza alternante di nodi e archi.
Gli archi e i nodi possono essere ripetuti.

# Trail
Un trail è una sequenza alternante di nodi, e archi non ripetuti.
Nel trail i nodi possono essere ripetuti, gli archi non possono essere ripetuti.
# Cammino
Il cammino è il walk senza nodi interni ripetuti e archi non ripetuti.
Un cammino è un Trail senza nodi interni ripetuti.
I nodi esterni possono essere quindi lo stesso nodo, in quel caso abbiamo un ciclo.
Un cammino orientato è un cammino contenente archi orientati.
# Ciclo
Un ciclo è un cammino con nodi estremi coincidenti.
Un ciclo orientato è un ciclo contenente archi orientati.

# Cammino Hamiltoniano
Un cammino Hamiltoniano è un cammino che tocca tutti i nodi di un grafo una e una sola volta.

# Cammino Euleriano
Un cammino Euleriano è un cammino che tocca tutti gli archi di un grafo una e una sola volta.


# Matching

Dato un grafo bipartito $G(N,A)$, un insieme $M$⊆$A$ si dice matching di $G$
se ogni nodo è incidente con al massimo un arco.
Matching perfetto $\implies$ ogni nodo è incidente con esattamente un arco.