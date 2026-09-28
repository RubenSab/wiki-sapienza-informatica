---
updated_at: 2026-09-25T10:38:47.154+02:00
---
# (Venturi)


# Classe REG (*[[linguaggio regolare|linguaggi regolari]]*) dei [[linguaggio|linguaggi]]

> Un linguaggio è **regolare** se esiste un automa che ne riconosce tutte le stringhe.

$$
\text{REG} = \{L \subseteq \Sigma^{\star}:\ \exists\ \text{DFA}\ M\ \text{t.c.}\ L(M) = L\}
$$

$L(M) = L$ significa che l'automa $M$ riconosce $L$.

## Esempio: progettare un DFA che accetta solo le stringhe che iniziano con "1"

$$
L = \{x \in \{0, 1\}^{\star}:\ x = 1y,\ y \in \{0, 1\}^{\star}\}
$$

```
             1
start -> q0 ---> [q1] --+
          |       ^     |
          | 0     |     | 0, 1
          v       +-----+
      +-> q2
 0, 1 |   |
      +---+
```

$q_{1}$ è lo stato finale.

> N.B.: Per far rifiutare la stringa, bisogna far andare l'automa in loop su un vicolo cieco, detto *stato pozzo*.

## Correttezza

Bisogna dimostrare entrambe le tesi:

1. $x \in L \implies M(\text{accetta})$
2. $x \notin L \implies M(\text{rifiuta})$

Si può dimostrare sia per induzione che con $\delta^{\star}$, ma è scontato e noioso.

# Esercizio per casa

$$
L = \{x \in \{0, 1\}^{\star}: \#_{1}(x) \geq 3\}
$$

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

# (Faralli)

> Un [[linguaggio]] regolare è definito dall'insieme di parole che possono essere combinate ([[sintassi]]) per generare [[regex (espressioni regolari)]].

Esempio con lo "Sheep Language": {"baaa", "baaaa", "baaaaa", "baaa...a"}

`baaa*` è l'espressione regolare che permette a un [[automa a stati finiti (DFA)]] di riconoscere input e produrre output per lo Sheep Language.


