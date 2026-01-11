---
updated_at: 2026-01-08T19:52:23.359+01:00
---
> Due vettori si dicono *linearmente indipendenti* su $K$, dati gli scalari $\lambda_{1}, \ldots, \lambda_{n} \in K$, se non esistono combinazioni lineari non [[spazio vettoriale#^a51465|banali]] $\lambda_{1} v_{1} + \ldots + \lambda_{n} v_{n}$ uguali a $0_{V}$ (origine/vettore nullo), altrimenti sono *linearmente indipendenti*.

Ad esempio $v_{1} = \binom{1}{0},\ v_{2} = \binom{0}{1}$ sono linearmente indipendenti: $\lambda_{1} v_{1} + \lambda_{2} v_{2} = \binom{\lambda_{1}}{0} + \binom{0}{\lambda_{2}} = \binom{\lambda_{1}}{\lambda_{2}}$. 

> In altri termini, l'unica combinazione lineare di $v_{1}, \ldots, v_{n}$ che è nulla è la combinazione lineare banale.

> Osservazione: $v_{1}, v_{2} \in K^{n} - \{0\}$ allora $v_{1}, v_{2}$ sono linearmente dipendenti $\iff$ sono **collineari**, ovvero l'uno proporzionale all'altro ($\exists \lambda \in K:\ v_{2} = \lambda v_{1}$).

Esempio in $\mathbb{R}^{3}$: $v_{1} = \begin{pmatrix} 2 \\ 2 \\ 2 \end{pmatrix},\ v_{2} = \begin{pmatrix} -3 \\ -3 \\ -3 \end{pmatrix}$. Si nota che $v_{2} = -\frac{3}{2} v_{1}$.

> Teorema: dei vettori (colonna) formano una matrice il cui [[determinante]] è **0** se se solo se sono **dipendenti**.

# Esempi

Nello [[spazio vettoriale]] $K^{n}$ consideriamo i vettori

$$
e_{1} = \begin{pmatrix} 1 \\ 0 \\ \vdots \\ 0 \end{pmatrix} \quad e_{2} = \begin{pmatrix} 0 \\ 1 \\ \vdots \\ 0 \end{pmatrix} \quad e_{j} = \begin{pmatrix} 0 \\ \vdots \\ 0 \\ 1 \\ 0 \\ \vdots \\ 0 \end{pmatrix} \quad e_{n} = \begin{pmatrix} 0 \\ \vdots \\ 0 \\ 1 \end{pmatrix}
$$

> Dimostrare che $e_{1}, \ldots, e_{n}$ sono linearmente indipendenti.

1. Consideriamo $\begin{pmatrix} \lambda_{1} \\ \vdots \\ \lambda_{n} \end{pmatrix} \in \mathcal{E}$.
2. Quindi $\lambda_{1} e_{1} + \ldots + \lambda_{n} e_{n} = 0 \in K^{n}$.
3. Questo si riscrive
   $$
   \begin{pmatrix} \lambda_{1} \\ 0 \\ \vdots \\ 0 \end{pmatrix} + \begin{pmatrix} 0 \\ \lambda_{2} \\ 0 \\ \vdots \\ 0 \end{pmatrix} + \ldots + \begin{pmatrix} 0 \\ \vdots \\ 0 \\ \lambda_{j} \\ 0 \\ \vdots \\ 0 \end{pmatrix} + \ldots + \begin{pmatrix} 0 \\ \vdots \\ 0 \\ \lambda_{n} \end{pmatrix} = \begin{pmatrix} 0 \\ \vdots \\ 0 \end{pmatrix} \iff \begin{pmatrix} \lambda_{1} \\ \vdots \\ \lambda_{n} \end{pmatrix} = \begin{pmatrix} 0 \\ \vdots \\ 0 \end{pmatrix} \iff \lambda_{1} = 0, \ldots, \lambda_{n} = 0
   $$
4. Ciò implica che $\mathcal{E} = \{0\}$, quindi $e_{1}, \ldots, e_{n}$ sono linearmente indipendenti.

---

$$
v_{1} = \begin{pmatrix} 1 \\ 0 \\ 1 \end{pmatrix} \quad v_{2} = \begin{pmatrix} 1 \\ 1 \\ 0 \end{pmatrix} \quad v_{3} = \begin{pmatrix} 0 \\ 1 \\ 1 \end{pmatrix}
$$

Mostrare che questi vettori sono linearmente indipendenti su $\mathbb{R}$ ([[campo]] degli scalari).

1. Si tratta di dimostrare che $\mathcal{E} = \left\{\begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}\right\}$ ma $\mathcal{E} = \left\{ \begin{pmatrix} \lambda_{1} \\ \lambda_{2} \\ \lambda_{3} \end{pmatrix} \in \mathbb{R}^{3}: \lambda_{1} v_{1} + \lambda_{2} v_{2} + \lambda_{3} v_{3} = 0 \right\}$.
2. Sia $\left\{\begin{pmatrix} \lambda_{1} \\ \lambda_{2} \\ \lambda_{3} \end{pmatrix}\right\} \in \mathcal{E}$, allora $\lambda_{1} v_{1} + \lambda_{2} v_{2} + \lambda_{3} v_{3} = 0 = \begin{pmatrix} \lambda_{1} + \lambda_{2} + 0 \\ 0 + \lambda_{2} + \lambda_{3} \\ \lambda_{1} + 0 + \lambda_{3}\end{pmatrix} \underset{\text{sistema lineare}}{=} \begin{pmatrix} 0 \\ 0 \\ 0 \end{pmatrix}$
   $\implies v_{1}, v_{2}, v_{3}$ sono linearmente indipendenti.