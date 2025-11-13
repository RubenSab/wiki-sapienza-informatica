---
updated_at: 2025-11-13T11:02:46.862+01:00
---

> Formalmente, una *permutazione* può essere vista come una mappa [[applicazione biiettiva o biiezione|mappa biiettiva]] tra due collezioni ordinate che contengono gli stessi elementi in ordine diverso o uguale (permutazione banale).

# Notazioni

## Notazione compatta

$$
\tau = (c\ a\ b\ d)
$$
Assumendo che gli elementi dell'insieme da permutare sono gli stessi permutati da $\tau$, cioè $\{a, b, c, d\}$, il primo elemento di $\tau$ indica che il primo elemento in ordine alfabetico ($a$) deve essere mappato a $c$, il secondo ($b$) a $a$, il terzo ($c$) a $b$ e l'ultimo ($d$) a $d$.

> N.B.: Ovviamente gli elementi permutati devono avere un ordine naturale per poter usare questa notazione.
 
## Notazione di Cauchy

$$
\tau = \begin{pmatrix} a\ b\ c\ d \\ c\ a\ b\ d\end{pmatrix}
$$

Ogni elemento della riga superiore mappa al suo elemento sottostante.

Invertire una permutazione è banale, basta invertire le righe:

$$
\tau^{-1} = \begin{pmatrix} c\ a\ b\ d \\ a\ b\ c\ d \end{pmatrix}
$$

e opzionalmente riordinare le colonne in ordine alfabetico rispetto alla riga superiore:

$$
\tau^{-1} = \begin{pmatrix} a\ b\ c\ d \\ b\ c\ a\ d \end{pmatrix}
$$

## Notazione ciclica

Oppure in notazione *ciclica*, la permutazione sopra di può scrivere $(a\ c\  b)(d)$, perché $a$ mappa a $c$, $c$ mappa a $b$, $b$ mappa ad $a$ e il ciclo si ripete, mentre $d$ rimane invariato: quindi si scrivono le due "isole" (cicli a supporto disgiunto) $a \to c \to b \to a$ e $d \to d$ separatamente. $(d)$ si può ignorare perché è un invariante.

La notazione ciclica ci permette di [[applicazione|applicare]] la permutazione a un determinato elemento dell'insieme che permuta, scrivendo la permutazione a sinistra e l'argomento tra parentesi tonde a destra.

$$
(a\ c\ b)\left(a\right) = c
$$
$$
(a\ c\ b)\left(b\right) = a
$$
$$
(a\ c\ b)\left(c\right) = b
$$
$$
(a\ c\ b)\left(d\right) = d
$$

> N.B.: **PIÙ PERMUTAZIONI SUCCESSIVE SI APPLICANO DA DESTRA A SINISTRA**.

# Permutazione ciclica

> È una permutazione che consiste in un **singolo** ciclo; tutti gli altri elementi permutati rimangono invariati.

Esempio:

$$
\rho = \begin{pmatrix} 1\ 2\ 3\ 4\ 5 \\ 1\ 3\ 2\ 4\ 5\end{pmatrix} = (1)(2\ 3)(4)(5) = (2\ 3)
$$

I cicli possono essere prefissati dalla loro lunghezza, in questo caso $\rho$ è un 2-ciclo o $(\star\ \text{ꙮ}\ \text{🥀})$ è un 3-ciclo.

> Due cicli (o permutazioni cicliche) si dicono *supporti disgiunti* se non hanno elementi in comune, formando due "isole" separate, ad esempio $(a\ b)\ (c\ d\ e)$.

> I 2-cicli si chiamano anche *trasposizioni*.

> Gli 1-cicli sono evidentemente invarianti.

# Quante sono le permutazioni di un [[teoria degli insiemi|insieme]] con [[cardinalità]] $n$?

$$
n \cdot(n-1) \cdot(n-2) \cdot \ldots \cdot 2 \cdot 1 = n!
$$

> N.B.: Per definizione, $0!=1$

Esempio: quante parole di lunghezza 8 posso formare con i caratteri V E R O N I C A? $8!$

Osservazione: e se invece se avessimo caratteri ripetuti come in M O N D O? Qui avremmo $\frac{5!}{2!}$ parole diverse di lunghezza 5, perché abbiamo contato ogni parola 2 volte distinguendo erroneamente le O, quindi dobbiamo eliminare tutti i modi diversi di ordinare le due O, cioè $2!$ (2). Questo è un esempio di [[disposizioni senza ripetizioni|disposizione senza ripetizione]].