
Ogni problema di Ottimizzazione Combinatoria ha una struttura matematica:
- Si ha un insieme base $B$ (contenente eventi elementari):
$$B=\{b_1,..., b_n\}$$
- Ogni soluzione ammissibile è un sottoinsieme $S \subseteq B$ di eventi elementari che rispettano le condizioni date.
- L’insieme delle soluzioni ammissibili è:
$$S = \{s_1,..., s_m\} \subseteq P(B)$$
- Ogni elemento di B ha un costo (o vantaggio) elementare $\{ c_i\}$
- Si ha una funzione di costo $c: S \rightarrow R$ 
- Si vuole trovare:
$$ \text{min } c(s): s \in S $$
- Ogni S può essere rappresentata con il suo vettore di incidenza $x^s$: 
$$ x^s = \begin{bmatrix}
 1 \\
1 \\
0 \\
\vdots \\
1
\end{bmatrix} $$

Possiamo riscrivere la funzione obiettivo:
$$ min \ \{ \ c^Tx : x \in V \subseteq \{0,1\}^n \ \} $$