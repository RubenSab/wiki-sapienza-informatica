---
updated_at: 2026-01-15T12:14:16.944+01:00
---
> Un'*[[applicazione]] lineare*, anche detta *trasformazione lineare*, è un [[omomorfismo]] tra [[spazio vettoriale|spazi vettoriali]] (definiti sullo stesso [[campo]]) che preserva le combinazioni lineari.

> N.B.: un'applicazione lineare [[applicazione biiettiva o biiezione|biiettiva]] è un [[isomorfismo]] tra spazi vettoriali.

Formalmente, dati gli spazi vettoriali $V$ e $V'$ definiti sul campo $K$, $f: V \to V'$ si dice applicazione lineare se gode delle proprietà di:

- *additività*: $\forall x, y \in V \quad f(x + y) = f(x) + f(y)$
- *omogeneità di grado 1*: $\forall x \in V, \forall \lambda \in K \quad f(\lambda x) = \lambda f(x)$

Equivalentemente, le due proprietà possono essere combinate nel *principio di sovrapposizione*, cioè la preservazione delle combinazioni lineari:

$$
\forall x_{i} \in V, \forall \lambda_{i} \in K \quad f(\lambda_{1} x_{1}  + \dots + \lambda_{n} x_{n}) = \lambda_{1} f(x_{1}) + \dots + a_{n} f(x_{n})
$$

> L'applicazione $V \xrightarrow{f} V$ è detta *endomorfismo* di $V$;
> se è biiettiva ($V \xleftrightarrow[f^{-1}]{f} V$), viene chiamata *automorfismo* di $V$.

> Osservazione: un'applicazione lineare iniettiva manda [[sottoinsiemi]] del dominio di [[vettori linearmente indipendenti]] in sottoinsiemi del codominio linearmente indipendenti.

Esempi di applicazioni/trasformazioni lineari in $\mathbb{R}^{2}$:

![[Pasted image 20260115114517.png]]
# Matrice associata

Dato che la trasformazione lineare $f$ trasforma allo stesso modo tutti i vettori, è utile descriverla come **"azione" sui vettori di una base** qualsiasi del dominio, in particolare della sua [[spazio vettoriale#^9fd07c|base canonica]].

> La matrice associata si costruisce mettendo uno dopo l'altro da sinistra a destra i risultati di $f$ applicata ai vettori della base **canonica**, uno alla volta.

Ad esempio la trasformazione in $\mathbb{R}^{2}$ da $V$, la cui base canonica è $\{\binom{1}{0}, \binom{0}{1}\}$:

![[Pasted image 20251218113513.png]]

a $V'$ la cui base è $\{\binom{2}{0.5}, \binom{0.4}{1.2}\}$:

![[Pasted image 20251218113905.png]]

si scrive $A = \begin{pmatrix} 2 & 0.4 \\ 0.5 & 1.2 \end{pmatrix}$.

La prima colonna mappa il vettore unità sull'asse $x$ (cioè $\binom{1}{0} \in V$) al vettore $\binom{2}{0.5} \in V'$, mentre la seconda colonna mappa il vettore unità sull'asse $y$ (cioè $\binom{0}{1} \in V$) al vettore $\binom{0.4}{1.2} \in V'$. Dato che tutti i vettori in $V$ sono combinazioni lineari dei vettori della base canonica, e tutti i vettori in $f(V) \subseteq V'$ sono combinazioni lineari di $\{\binom{2}{0.5}, \binom{0.4}{1.2}\}$, la trasformazione è completamente rappresentabile come la matrice associata.

> Infatti vale che:

$$
V \xrightarrow{f} V' \quad \quad Im(f) = f(V) = \{Av,\ v \in V\} \subseteq V'
$$

> N.B: l'immagine di $f$ è un [[sottospazio vettoriale]] di $V'$.

# Kernel

> Il *Kernel*, o *nucleo* di $f$ è l'insieme $\ker(f) = \{v \in V: f(v) = 0_{V'}\}$, cioè **l'insieme di vettori di $V$ che, se trasformati da $f$, puntano all'origine di $V'$**. Per definizione $\text{ker}(f)$ è un sottospazio vettoriale di $V$.

Per trovare il kernel di un'applicazione lineare, basta trovare i vettori che puntano allo zero di $V'$ risolvendo il [[sistema di equazioni lineari]] $v \cdot M = 0_{V'}$, dove $v \in V$ e $M$ è la matrice associata.

Ad esempio, in $\mathbb{R}^{2}$ con $M = \begin{pmatrix} 2 & 0 \\ 1 & 3 \end{pmatrix}$:

$$
\begin{pmatrix} x \\ y \end{pmatrix} \begin{pmatrix} 2 & 0 \\ 1 & 3 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix} \quad \to \quad x \begin{pmatrix} 2 \\ 1 \end{pmatrix} + y \begin{pmatrix} 0 \\ 3 \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix} \quad \to \quad \begin{cases} 2x + y = 0 \\ x + 3y = 0 \end{cases} \quad \to \quad \begin{pmatrix} x \\ y \end{pmatrix} = \begin{pmatrix} 0 \\ 0 \end{pmatrix}
$$

Quindi $\ker\left(\begin{pmatrix} 2 & 0 \\ 1 & 3 \end{pmatrix} \right) = \left\{ \begin{pmatrix} 0 \\ 0 \end{pmatrix} \right\}$ (il sottospazio vettoriale triviale): solo $\begin{pmatrix} 0 \\ 0 \end{pmatrix}$ punta all'origine di $V'$.

# Teorema della dimensione

Se $V$ e $V'$ hanno [[spazio vettoriale#^9b5e71|dimensione]] finita, vale che:

$$
\dim(\ker(f)) + \dim(\text{Im}(f)) = \dim(V) \iff f\ \text{è lineare}
$$

> N.B.: Ciò può essere usato come un criterio per scoprire se una trasformazione è lineare.