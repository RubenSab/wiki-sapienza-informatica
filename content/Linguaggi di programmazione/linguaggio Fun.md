---
updated_at: 2026-10-15T10:48:39.036+02:00
---
È un superlinguaggio del [[linguaggio Exp]]. La sua grammatica contiene tutti i suoi elementi e le funzioni unarie.

$$
M, N ::= 5 \mid 7 \mid \ldots \mid N+M \mid \text{let}\ x = M\ \text{in}\ N \mid Fn\ x\implies M \mid MN
$$

> $MN$ è l'applicazione.

L'applicazione di [[funzione]] è associativa a sinistra: ad esempio $(MN)L$ vuol dire $M$ passato a $N$ applicato a $L$. Cioè se avessimo $\underset{M}{\underbrace{(\text{Fn}\ x \implies x)}}\underset{N}{\underbrace{(\text{Fn}\ x \implies x+1)}}\underset{L}{\underbrace{7}}$, dovremmo passare $N$ (la funzione successore) come oggetto a $M$ (la funzione identità). Otteniamo $N$ applicato a $7$, quindi $MNL$ restituisce $8$.

Dobbiamo cambiare il dominio semantico $E$ di $E \vdash M \rightsquigarrow v$ rispetto a com'era in Exp.

Il problema di $MN$ è così definito si può applicare un intero a un altro intero, non solo funzioni, ad esempio $5\ 7$ (5 applicato a 7, non 57). Oppure $5(\text{Fn}\ z \implies z + 1)$ (funzione applicata a un intero) che è [[sintassi|sintatticamente]] ben costruito ma non ha senso. La [[semantica]] operazionale non potrà dargli un valore, perché l'albero di derivazione si bloccherà. Serve la [[ŧeoria dei tipi]] per risolvere parzialmente questo problema, ma per ora siamo in un universo non *tipato*.

Esempi:

$$
\underbrace{(\text{Fn } x \implies (\text{Fn } z \implies xz))}_{M}
\underbrace{(\text{Fn } y \implies y+1)}_{N}
\underbrace{7}_{L}
$$

$$
\rightsquigarrow \underbrace{(\text{Fn } z \implies ((\text{Fn } y \implies y+1)z))}_{MN}
\underbrace{7}_{L}
$$

$$
\rightsquigarrow (\text{Fn } y \implies y+1)\,7
$$

$$
\rightsquigarrow 7+1
$$

$$
\rightsquigarrow 8
$$

---

$$
(\text{Fn} x \implies (\text{Fn}\ y \implies x)) 7 \rightsquigarrow \text{Fn}\ y \implies 7
$$

---

Possiamo creare funzioni binarie con la *curryficazione* componendo funzioni *unarie*.

$$
\text{Fn}\ x \implies \text{Fn}\ y \implies x + y
$$

Il curry di una funzione è da $A \land B \to C$ a $A \to (B \to C)$ e la uncurryficazione è il contrario.

---

Bisogna cambiare l'insieme $\text{val}$:

$$
\text{val} = \mathbb{N} \cup (\text{Val} \times \text{Fun} \times \text{Exp})
$$

I valori funzionali saranno triple $(X, M, E)$ definite **chiusure**: variabile, elemento del linguaggio (pezzo di sintassi) e ambiente.

Regole di inferenza aumentate: (eager statica)

$$
\begin{cases}
E \vdash k \to k \\
E \vdash x \to v\ (\text{se}\ E(x)=v) \\
\frac{E \vdash M \to v_{1}\quad E \to N \to v_{2}}{E \vdash M + N \to v}\ (\text{se}\ v_{1} + v_{2} = v) \\
\frac{E \vdash M \to v\quad E(x, v) \vdash N \to v'}{E \vdash \text{let} x = M\  \text{in}\ N \to v'}
\end{cases}
$$

$$
E \vdash \text{Fn}\ x \implies M \rightsquigarrow (x, M, E)
$$

Call by value

$$
\frac{E \vdash M \to (x, M', E')\quad E(x, v) \vdash N \to v}{E \vdash MN \to}
$$

Let non serve più

$$
\text{let}\ x = M\ \text{in}\ N \equiv (\text{Fn}\ x \implies N) M
$$

All'estremo, si può fare a meno del + e a meno dei numeri, usando i [[numeri di Church]]. Si ottiene il [[lambda calculus]].