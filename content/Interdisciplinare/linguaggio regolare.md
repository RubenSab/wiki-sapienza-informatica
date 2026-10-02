---
updated_at: 2026-10-02T10:01:07.191+02:00
---
# Classe REG dei [[linguaggio|linguaggi]]

> Un [[linguaggio]] è **regolare** se esiste un [[macchine di Moore e Mealy|macchina a stati finiti]] che ne riconosce tutte le stringhe.

$$
\text{REG} = \{L \subseteq \Sigma^{\star}:\ \exists\ \text{DFA}\ M\ \text{t.c.}\ L(M) = L\}
$$

$L(M) = L$ significa che l'automa $M$ riconosce $L$.

# Definire un linguaggio regolare tramite la funzione di transizione estesa

> Per definire rigorosamente un $L(DFA)$, cioè il linguaggio regolare associato ad un DFA, si usa la **[[funzione]] di transizione estesa**.

$$
\delta:\ Q \times \Sigma \to Q
$$

$$
\delta^{\star}: Q \times \Sigma^{\star} \to Q
$$

Così un linguaggio regolare si può definire come l'[[insieme]] $\{\sigma \in \Sigma:\ \delta^{\star}(\sigma) \in F\}$.

Delta star si può definire ricorsivamente in modo elegante partendo da $\delta$:

$$
\begin{cases}
\delta^{\star}(q, \varepsilon) = \delta(q, \varepsilon) \\
\delta^{\star}(q, ax) = \delta^{\star}(\delta(q, a), x) \quad a \in \Sigma,\ x \in \Sigma^{\star}
\end{cases}
$$

> N.B.: La stringa vuota $\varepsilon$ sta in $\Sigma^{\star}$ ([[Star di Kleene]] di $\Sigma$) per definizione, ma non per forza nel linguaggio, che è un sottoinsieme di $\Sigma^{\star}$.

$$
a \in \Sigma \quad x \in \Sigma^{\star}
$$

> Il linguaggio riconosciuto da un DFA $M = (Q, \Sigma, \delta, q_{0}, F)$ è $L(M) = \{x \in \Sigma^{\star}:\ \delta^{\star}(q_{0}, x) \in F\}$.

# Proprietà dei linguaggi regolari

I linguaggi regolari hanno una chiusura rispetto ad alcune [[operazioni fra gli insiemi|operazioni]]:

- **unione**: $L_{1} \cup L_{2} = \{x \in \Sigma^{\star}:\ x \in L_{1} \lor x \in L_{2}\}$
- **intersezione**: $L_{1} \cap L_{2} = \{x \in \Sigma^{\star}:\ x \in L_{1} \land x \in L_{2}\}$
- **complemento**: $\overline{L_{1}} = \{x \in \Sigma^{\star}: x \in L_{1}\}$
- **concatenazione**: dati $x=a_{1}, \ldots, a_{n}$ e $y=b_{1}, \ldots, b_{n}$, si ha $L_{1} \circ L_{2}$ = $a_{1}, \ldots, a_{n}\ b_{1}, \ldots, b_{n}$; ricorsivamente:

$$
\begin{cases}
x \varepsilon = x, \quad x, y \in \Sigma \\
x(ya) = (xy)a, \quad a \in \Sigma
\end{cases}
$$

$$
L_{1} \circ L_{2} = \{xy:\ x \in L_{1}, y \in L_{2}\}
$$

- **potenza** (è tipo il [[prodotto cartesiano]]):

$$
\begin{cases}
x^{0} = \varepsilon \\
x^{n+1} = x^{n} x;\ n \geq 0
\end{cases}
$$

Per i linguaggi

$$
\begin{cases}
L^{0} = \{\varepsilon\} \\
L^{n+1} = L^{n} \circ L; n \geq 0
\end{cases}
$$

## Dimostrazioni

### Unione

- Tesi: $L_{1} = L_{1}(M_{1})$ e $L_{2} = L_{2}(M_{2})$
- Ipotesi: $L_{1} \cup L_{2}$

> Si assume che $\Sigma_{1} = \Sigma_{2}$.

> Difficoltà: non posso eseguire $M_{1}$ e $M_{2}$ su $x$ e vedere che succede. In qualche modo invece, bisogna costruire un DFA che li "esegue in parallelo".

Devo definire $M = (Q, \Sigma, \delta, q_{0}, F)$ tale che:

- $Q = Q_{1} \times Q_{2}$
- $\delta((r_{1}, r_{2}), a) = (\delta_{1}(r_{1}, a),\ \delta_{2}(r_{2}, a))$
- $q_{0} = (q_{1}, q_{2})$
- $F = (F_{1} \times Q_{2}) \cup (F_{2} \times Q_{1}) = \{(r_{1}, r_{2}):\ r_{1} \in F_{1} \lor r_{2} \in F_{2}\}$ (se uno dei due stati $Q_{1}$ o $Q_{2}$ sono finali non ci interessa dell'altro, stiamo ragionando sull'unione)

Il resto della dimostrazione è inutile per il corso.

## Ri-dimostrazioni usando gli [[automa non deterministico a stati finiti (NFA)|NFA]]
### REG è chiuso per $\cup$

Dati due NFA $N_{1},\ N_{2}$ che riconoscono rispettivamente $L_{1},\ L_{2}$ costruisco un NFA $N$ che riconosce $L_{1} \cup L_{2}$.

![[Pasted image 20261002090311.png]]

### REG è chiuso per $\circ$ (concatenazione)

Dati due NFA $N_{1},\ N_{2}$ che riconoscono rispettivamente $L_{1},\ L_{2}$ costruisco un NFA $N$ che riconosce $L_{1} \circ L_{2}$.

![[Pasted image 20261002090846.png]]

### REG è chiusa per $\star$

Dato un NFA $N_{1}$ tale che $L(N) = L$ (che riconosce $L$) costruisco un NFA $N^{\star}$ tale che $L(N^{\star}) = L^{\star}$.

Mettiamo conto che $N$ riconosce $L=\{0, 1\}$, implementato con un albero di caratteri:

![[Pasted image 20261002095514.png|204]]

Per fare un DFA che riconosce $L^{2} = \{00, 01, 10, 11\}$ bisogna copiare l'albero di $N$ e "attaccarlo" su ogni sua foglia:

![[Pasted image 20261002095646.png|212]]

Si potrebbe provare a ripetere il procedimento all'infinito per $N^{\star}$:

![[Pasted image 20261002095908.png|310]]

Ma questo non sarebbe un DFA, perché ha stati infiniti.

Però si può costruire un NFA analogo a questo partendo dal caso iniziale $\{0, 1\}$:

![[Pasted image 20261002100106.png|165]]

Nel caso generale, vale che:

![[Pasted image 20261002095257.png]]

