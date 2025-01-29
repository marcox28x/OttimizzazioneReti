## Definizione Grafo

Definiamo un grafo come $G(N,A)$, dove

$$N = \{v_1, v_2,...,v_n\} \text{ è l'insieme di tutti i nodi di } G.$$
$$A = \{e_1, e_2, ...,e_n\} \text{ è l'insieme di tutti gli archi di } G.$$

---
## Definizione Albero Ricoprente

$H(N,T)$ rappresenta un sotto-grafo di $G(N,A)$ con le seguenti caratteristiche:
- Include tutti i nodi da $G(N,A)$ (sono gli stessi vertici).
- deve essere connesso (deve esserci un cammino da un nodo ad un altro).
- Non contiene cicli.
---
## Costi

### Costo di un insieme di archi

Definiamo il costo di un insieme di archi $F \subseteq A$ come:
$$c(F) = \sum_{uv \in F} c_{uv}$$
Praticamente stiamo dicendo che il costo di un insieme di archi è la somma dei costi dei singoli archi dell'insieme.
$c(F)$ è la funzione costo del sotto-insieme di archi $F$.

### Costo di un albero ricoprente

Definiamo il costo di un albero ricoprente $H(N,T) \text{ di } G(N,A)$
$$c(H(N,T)) = c(T) = \sum_{uv \in T} c_{uv}$$
$H(N,T)$ è l'albero ricoprente del grafo $G(N,A)$ ed il suo costo è quindi la somma dei costi degli archi $uv \in T$ 

## Minimo della funzione costo
Il minimo della funzione costo $c(H(N,T))$ è nel punto $c(H,(N,T^*))$.
$$c(H(N,T^*) \leq c(H,(N,T)) \quad \forall \; \text{albero ricoprente } H(N,T)$$
---
## Il problema:

Dato un grafo $G(N,A)$ non orientato e connesso, con costi sugli archi dati da $c_{uv}$ per ogni arco $uv \in A$ trovare un albero ricoprente di costo minimo $(H,N^{*})$. 

---

## Teorema del cammino singolo

Se $G(N,A)$ è un albero allora per ogni coppia di nodi $\{u,v\} \subseteq N$ esiste un solo cammino $P$ che connette $u$ a $v$

### Dimostrazione

Supponiamo per assurdo che esistano due cammini distinti $P_1$ e $P_2$ in $G(N,A)$ che connettono $u$ e $v$. Preso  $t \in P_1$ e  $t \in P_2$ , sia $ty$ il primo arco di $P_1$ . ($ty$ esiste perché $P_1 \neq P_2$ . $ty$ è il primo arco che i cammini $P1$ e $P2$ non hanno in comune)  

- Se $y \in P_2$ , esiste un sotto-cammino ${P_2}^{ty}$ tra $t$ e $y$ in $P_2$ che concatenato all'arco $ty$ forma un ciclo. Arriviamo ad una contraddizione perché un albero non può avere cicli.
- Se $y \notin P_2$ , sia $w$ il primo nodo di $P_1$ , successivo a $t$ con $w \in P_2$ . Il cammino tra $t$ e $w$ su $P_1$ e il cammino tra $t$ e $w$ su $P_2$ hanno in comune solo gli estremi, quindi definiscono un ciclo in $G(N,A)$. $\quad \square$ 

---

## Teorema delle due foglie

Un albero $H(N,T)$, con $|N| \geq 2$ , contiene almeno due foglie.
*Ovvero, un albero con almeno due nodi contiene almeno due foglie.*

### Dimostrazione
Chiamiamo $P$ il cammino più lungo dell'albero $H(N,T)$ . Pertanto il cammino $P = (u,(u,z),z,...,v)$ sarà il cammino con il massimo numero di archi e $u$ e $v$ sono due foglie.
Dimostriamo per u.
Se, per assurdo, $u$ non è una foglia $\implies$ esiste $w \neq z$ tale che $(w,u) \in T$ .
Stiamo anche dicendo che il nodo $u$ ha sicuramente due archi: $(u,z)$ e $(u,w)$ .
Ora dobbiamo analizzare due situazioni:
- $w \notin P$
- $w \in P$

Se $w \notin P$  $\implies$ possiamo creare un nuovo cammino $P'$ che parte da $w$ passa per $u$ e percorre tutto $P$ .
$$P' := (w,u) \cup P = (w,(w,u),u,(u,z),z,...,v)$$ 
Il cammino $P'$ contiene più archi del cammino $P$ , ma questo contraddice la nostra ipotesi ($P$ è il cammino più lungo). Abbiamo una contraddizione.

Se $w \in P$ $\implies$ il nodo $w$ si trova qualche parte nel cammino $P$. In pratica il cammino P sarà scritto in questo modo:
$$P = (u,(u,z), z,..., w,..., v)$$
Esiste quindi in $H$ un cammino $P'$ di estremi $u$ e $w$ che non contiene l'arco $(u,w)$:

$$P’ = (u,(u,z), z,...,w)$$
Ma quando è stata fatta l'ipotesi per assurdo, è stato specificato che l'albero $H$ dovesse contenere l'arco $(u,w)$ .   
$$C = (w,u) \cup P’ = (w,(w,u),u,(u,z),z,...,w)\implies C \ \text{è un ciclo di } H$$
Unendo le ultime due considerazioni sono riuscito a trovare un ciclo, il che ci porta ad una contraddizione.

---
## Teorema del numero di archi
Un albero $H(N,T)$ ,  contiene esattamente $|N| - 1$ archi.

### dimostrazione
Utilizziamo il **principio di induzione** per dimostrare il teorema.

Passo base: $|N| = 1$

Se $|N| = 1$  e  $T = \emptyset$ $\implies$  La formula $|T| = |N| - 1$ diventa:
$$0 = 1 - 1$$
Il passo base è verificato.

Passo induttivo:
Assumiamo che il teorema valga per un albero con k nodi $(|N| = k)$ . Questo significa che:
$$ |T| = k - 1 $$
Dobbiamo dimostrare che il teorema vale anche per un albero $N'$ con $k + 1$ nodi $(|N'| = k + 1).$

Iniziamo con un albero $H(N,T)$:
- Ha $|N| = k$ nodi.
- Ha $|T| = k -1$ archi.

Prendiamo una foglia $v$ dall'albero $H$. Essendo H un albero, contiene necessariamente almeno una foglia.
Costruiamo $H' = (N',T')$, aggiungendo un nodo $u$ e l'arco $(u,v)$ ad $H$.
$H'$ è connesso e non contiene cicli $\implies$ $H'$ è un albero.

Abbiamo anche che:
$$|N'| = |N| + 1 = k+1$$
$$|T'| = |T| + 1 = k - 1 + 1= k$$
quindi:
$$|T'| = |N'| - 1$$
$\square$

---

## Teorema del ciclo fondamentale

Dato un albero ricoprente $H(N,T)$ di $G(N,A)$ abbiamo che per ogni arco $f \in A \setminus T$ 
il sotto-grafo $H(N,T \cup \{f\})$ contiene un solo ciclo $C$.

### Dimostrazione

Ogni ciclo $C$ di $H(N,T \cup \{f\})$ deve contenere l'arco f
( Se un ciclo $C$ non contiene $f$  allora avrei un ciclo in $H(N,T)$, ma, essendo un albero, è impossibile. )
Siano $u$ e $v$ gli estremi dell'arco $f \in A \setminus T$ 
Ogni ciclo di $H(N,T \cup \{f\})$ è univocamente associato a un cammino $P$ da $u$ a $v$ in $H(N,T).$
Ma per il teorema del cammino singolo esiste un solo cammino da $u$ a $v$ in $H(N,T)$
e quindi esiste un solo ciclo in $H(N,T \cup \{f\})$ ,
il ciclo fondamentale $C(f,T)$ di $G(N,A)$

---

## Teorema dello scambio

Dato un albero ricoprente $H(N,T)$ di $G(N,A)$, un arco $f \in A-T$ e un arco $g \in C(f,T)$, abbiamo che $H(N,(T \cup \{f\}) \setminus \{g\})$ è un albero ricoprente $G(N,A)$

### dimostrazione

Per il teorema ciclo, $H(N,T \cup \{f\})$ contiene esattamente un ciclo fondamentale $C(f,T)$
Eliminando $g = (u,v) \in C(f,T)$ si distrugge $C(f,T)$ senza aggiungere nuovi cicli.
Quindi:
$H(N,T \cup \{f\} \setminus \{g\})$ non contiene cicli. Ma è connesso?
Supponiamo che $H(N,T \cup \{f\} \setminus \{g\})$ non sia connesso.
Allora esistono due nodi $z$ e $w$ connessi in $H(N,T)$ ma non in $H(N,T \cup \{f\} \setminus \{g\})$
Allora il cammino unico che univa $z$ a $w$ in $H(N,T)$ conteneva l'arco $g$
$z$ e $w$ sono in diverse componenti connesse di $H(N,T \cup \{f\} \setminus \{g\})$
$u$ e $z$ sono connessi in $H(N,T \cup \{f\} \setminus \{g\})$
$v$ e $w$ sono connessi in $H(N,T \cup \{f\} \setminus \{g\})$
$u$ e $v$ sono in diverse componenti connesse di $H(N,T \cup \{f\} \setminus \{g\})$
ma $u$ e $v$ sono connessi, per costruzione, in $H(N,T \cup \{f\} \setminus \{g\})$ tramite f
contraddizione
quindi anche $H(N,T \cup \{f\} \setminus \{g\})$ è connesso


Vediamo la dimostrazione **passo passo**, cercando di spiegare bene **cosa succede** e **perché**.

---

## 1) Lo scenario iniziale

- Abbiamo un **grafo connesso** $G(N,A)$ e un suo **albero ricoprente** $H(N,T)$.
    
    - “Albero ricoprente” significa che $T \subseteq A$, collega tutti i N nodi e non ha cicli.
- Prendiamo un **arco** $f \in A - T$, cioè un arco **fuori** dall’albero T. Aggiungiamo $f$ a $T$:
    
     $T \cup \{f\}$.
    
    In questo modo otteniamo un grafo **non più albero** (perché quando aggiungi un arco a un albero, crei un ciclo).
    

---

## 2) Comparsa del “ciclo fondamentale” $C(f,T)$

**Teorema (del ciclo fondamentale):**  
Quando aggiungi un arco $f$ a un albero $T$, si crea **esattamente un** ciclo, detto _ciclo fondamentale, indicato con $C(f,T)$.

- Intuitivamente: in un albero $T$ c’è **unico cammino** che unisce le estremità di $f$. Aggiungendo $f$, chiudi quel cammino in un “anello” (ciclo).

Dunque, nel nuovo grafo $H(N,T \cup \{f\})$ c’è **esattamente** il ciclo $C(f,T)$.

---

## 3) Rimuovere $g \in C(f,T)$ distrugge il ciclo senza crearne altri

Scegliamo **un arco** $g \in C(f,T)$ (quindi $g$ sta proprio nel ciclo fondamentale). Rimuoviamolo:

$(T \cup \{f\}) \setminus \{g\}$.

### Perché scompare **quel** ciclo?

- In un ciclo, **se togli un arco**, rompi l’anello: non hai più un giro chiuso.
- Quindi **distruggi** $C(f,T)$.

### Perché non compaiono cicli nuovi?

- Abbiamo tolto un arco **del ciclo**. Il resto del grafo era un albero $T$ (senza cicli) + l’arco $f$. Non c’è modo di formare un nuovo ciclo perché, appunto, rimuovendo un arco dal _solo_ ciclo esistente lo rompi e non crei altri giri.

Dunque, dopo aver rimosso $g$,

$H(N,(T \cup \{f\}) \setminus \{g\})$

non contiene alcun ciclo (**è aciclico**).

---

## 4) Resta da dimostrare che il grafo è ancora connesso

Abbiamo un grafo con $N$ nodi e $N-1$ archi (perché ne avevamo $N-1$ in $T$, ne abbiamo aggiunto 1 e tolto 1). Se dimostriamo che è **anche connesso**, abbiamo esattamente un **albero ricoprente**.

### Strategia: per assurdo

Supponiamo che

$H(N,(T \cup \{f\}) \setminus \{g\})$

**non** sia connesso. Allora esistono almeno due componenti connesse. Prendiamo due nodi $z$ e $w$ che:

1. **Nel vecchio albero** $H(N,T)$ (che è connesso) erano raggiungibili: esiste un cammino $z \to \dots \to w$
2. **Nel nuovo grafo** $H(N,(T \cup \{f\}) \setminus \{g\})$ non sono più raggiungibili (stanno in componenti diverse).

---

### 5) Il cammino $z \to w$ in $T$ usava necessariamente $g$

Poiché $z$ e $w$ erano connessi in $T$ (albero), esisteva **un unico** cammino in $T$ che li univa (nessun ciclo, quindi un solo percorso possibile).

Ora, se quel cammino **non** avesse contenuto $g$, allora in

$(T \cup \{f\}) \setminus \{g\}$

sarebbe rimasto tutto quel cammino intatto, e $z$ e $w$ risulterebbero ancora connessi. Ma noi abbiamo ipotizzato che nel nuovo grafo **non** lo siano. Quindi **per forza** quel cammino conteneva $g$.

---

### 6) Conseguenze dell’aver rimosso $g$

- Togliendo $g$, il vecchio cammino $z \to \dots \to w$ si rompe.
- Dunque $z$ e $w$ finiscono (per ipotesi) in due componenti diverse.

Contemporaneamente, nel nuovo grafo, l’arco $f$ è ancora presente e collega i due nodi (diciamo) $u$ e $v$ (cioè le estremità di $f$).

Ma attenzione: $g = (u,v)$ era **anche lui** dentro il ciclo $C(f,T)$. Se $g$ è $(u,v)$, significa che nel vecchio albero $T$ c’era un cammino che univa $u$ e $v$ passando per una serie di nodi, **incluso** $g$.

---

### 7) Contraddizione: perché $u$ e $v$ risultano ancora connessi

Nel nuovo grafo (dopo la rimozione di $g$):

1. **$f$ è attivo**: c’è un arco diretto $u \leftrightarrow v$.
2. **(Quasi tutto) il vecchio albero** $T$ è presente, tranne $g$.

Se nel passaggio precedente abbiamo dedotto che $u$ e $v$ si trovano in due componenti diverse, allora sarebbero “irraggiungibili” l’uno dall’altro. **Ma** l’arco $f$ (che fa proprio $u \leftrightarrow v$) è nel grafo! Quindi, per costruzione, $u$ e $v$ devono poter essere collegati direttamente via $f$.

Questo è un **conflitto** logico: prima diciamo “sono in componenti diverse” (quindi non connessi), poi osserviamo che “hanno un arco diretto $f$” (quindi **sono** connessi). Impossibile.

---

### 8) Il grafo è connesso, e dunque è un albero

Abbiamo trovato una contraddizione partendo dall’assunto che “il nuovo grafo non è connesso”. Quindi:

- **Il nuovo grafo deve essere connesso.**
- Sappiamo già che non ha cicli (vedi punto 3).
- Ha $N−1$ archi e $N$ nodi.

Ne consegue che $H(N,(T \cup \{f\}) \setminus \{g\})$ è un albero ricoprente** di $G(N,A)$.

---

## Ricapitolando in poche parole

1. **Aggiungi $f$** a un albero: compare un **unico ciclo** $C(f,T)$.
2. **Togli un arco $g$ da quel ciclo: rompi $C(f,T)$, niente cicli nuovi, rimani con $N-1$ archi**.
3. Se, per assurdo, il grafo risultasse **non connesso**, dovresti trovare due nodi che prima erano uniti ma ora no. L’unico modo è che il loro vecchio cammino usasse $g$. Ma allora, l’arco $f$ fornisce un percorso alternativo che **ri-collega** quei nodi, generando contraddizione.
4. Quindi il grafo **resta connesso** ed è anche aciclico: è di nuovo un albero ricoprente.

**Fine.**

---

Un'albero $T$ è parzialmente ottimo rispetto al costo $c$ se esiste un albero ricoprente di costo minimo $H(N,T^*)$ e $T \subseteq T^*$ .



Teorema parzialmente ottimo costo minimo

Ogni albero ricoprente $H(N,T)$ di $G(N,A)$ parzialmente ottimo è un albero ricoprente di costo minimo di $G(N,A)$

Poiché $H(N,T)$ è parzialmente ottimo ed è un albero ricoprente, esiste $T^*$ albero ricoprente di costo minimo tale che $T \subseteq T^*$, ma siccome $|T| = |N| - 1 = |T^* |$
$H(N,T)$ è un albero ricoprente di costo minimo.


Teorema di accrescimento
Se $H(S,T)$ è una foresta parzialmente ottima di $G(N,A)$ tale che:
- $M = uv \in A - T : H' (S \cup \{u,v\}, T  \cup \{uv\})$ è una foresta
- $wy$ è un arco di costo minimo in M
allora la foresta $H' (S \cup \{u,v\}, T  \cup \{uv\})$ è parzialmente ottima




# Kruskal

Costruisci una sequenza di foreste $H(S,T)$ con $S \subseteq N$
- Inizia con $S=\{\}$ e $T=\{\}$: foresta in $G(N,A)$
- Ad ogni passo: 
	1. aggiungi a $T$ l’arco di costo minimo $wy \in A-T$ tale che $H’(S \cup \{w,y\},T \cup \{wy\})$ sia aciclico
	2. aggiungi ad $S$ i nodi $w$ ed $y$.


S