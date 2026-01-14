---
updated_at: 2026-01-14T11:33:34.692+01:00
---
Consideriamo il [[sistema di equazioni lineari]] $AX = B$.

> Chiamiamo *matrice completa* $(A \mid B) \in \mathcal{M}_{m, n+1}$ la matrice che si ottiene accostando orizzontalmente la [[spazio vettoriale di matrici|matrice]] $A$ dei coefficienti e il [[spazio vettoriale|vettore]] $B$ delle indeterminate.

Esempio:

$$
A = \begin{pmatrix} 1 & 2 \\ 3 & 4 \\ 5 & 6 \end{pmatrix} \in \mathcal{M}_{3,2} \quad B = \begin{pmatrix} 7 \\ 8 \\ 9 \end{pmatrix} \in \mathcal{M}_{3, 1} \quad A \mid B = \begin{pmatrix} 1 & 2 & 7 \\ 3 & 4 & 8 \\ 5 & 6 & 9 \end{pmatrix} \in \mathcal{M}_{3,3}
$$

Ricordiamo che risolvere $AX = B$ equivale a trovare tutti gli $X = \begin{pmatrix} x_{1} \\ \vdots \\ x_{n}\end{pmatrix}$ con $AX = B$.

# Definizioni preliminari all'algoritmo

#todo rispiega da [wikipedia](https://en.wikipedia.org/wiki/Matrix_(mathematics)#cite_note-FOOTNOTELang1986[httpbooksgooglecombooksidc_NEBAAAQBAJpgPA71_71]-31)
## Operazioni elementari lecite sulle righe della matrice completa ($A \mid B$)

- Permutare righe;
- Sostituire una riga con un suo multiplo scalare non nullo $r \mapsto \lambda r$ con $\lambda \in K^{X}$;
- Sostituire una riga con la stessa più un multiplo scalare di un altra $r \mapsto r + \lambda r'$;

## Convenzioni di notazione

- Scriviamo $(A \mid B) \sim (A' \mid B') \iff \text{Sol}(A \mid B) = \text{Sol}(A' \mid B')$;
- Scriviamo inoltre $(A \mid B)\ {\smile \atop \frown}\ (A' \mid B')$ se posso ottenere la seconda dalla prima applicando un minimo finito di operazioni elementari lecite sulle righe ("la matrice a destra è costruibile lecitamente da quella a sinistra");

> Osservazione: ${\smile \atop \frown}$ è una [[proprietà, tipi di relazioni e ordini|relazione d'equivalenza]].

> Osservazione: $A {\smile \atop \frown} B \implies \text{rg}(A) = \text{rg}(B)$.

> Una matrice completa è detta *a gradini* o *a scalini* se è come questa

$$
\begin{pmatrix}
0 & 0 & 0 & 1 & * & * & * & * & * & * & * & * & * \\
0 & 0 & 0 & 0 & 0 & 1 & * & * & * & * & * & * & * \\
0 & 0 & 0 & 0 & 0 & 0 & 1 & * & * & * & * & * & * \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & * & * \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & * \\ 
\end{pmatrix}
$$

oppure con una o più righe composte solo da zeri sia sopra che sotto; inoltre riga del primo gradino può anche avere un $1$ a sinistra senza alcuno zero. Una matrice a gradini banale contiene **solo** zeri.

> Una matrice a gradini si dice *ridotta* se sopra a tutti gli $1$ ci sono zeri, ad esempio:

^dc0740

$$
\begin{pmatrix}
0 & 0 & 0 & 1 & * & 0 & 0 & * & * & * & 0 & 0 & * \\
0 & 0 & 0 & 0 & 0 & 1 & 0 & * & * & * & 0 & 0 & * \\
0 & 0 & 0 & 0 & 0 & 0 & 1 & * & * & * & 0 & 0 & * \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & 0 & * \\
0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 0 & 1 & * \\ 
\end{pmatrix}
$$

> Gli $1$ che definiscono i gradini vengono chiamati *pivot*.

^3294b5

## Teorema di Gauss

- In ogni classe di $\smile \atop \frown$ di matrici complete $(A \mid B)$ esiste un'unica matrice a gradini ridotta.
- $(A \mid B)\ {\smile \atop \frown}\ (A' \mid B') \implies (A \mid B) \sim (A' \mid B')$.

>N.B.: Contro-intuitivamente, l'[[algoritmo]] di Gauss è la dimostrazione di questo teorema, non il contrario.

# Esercizi

## 1.

$$
(A \mid B) = \begin{pmatrix} 1 & 1 & -1 & -2 & 4 \\ 1 & 0 & -1 & 0 & 0 \\ 0 & 1 & 0 & 1 & -2 \end{pmatrix} = \begin{cases} x + y - z - 3t = 4 \\ x - z = 0 \\ y + t = -2 \end{cases}
$$

Applichiamo a catena le operazioni elementari lecite sulle righe, annotando quella usata sotto il simbolo "di costruzione di matrici" $\smile \atop \frown$, fino a raggiungere una matrice **completa** e **ridotta**.

$$
\begin{pmatrix} 1 & 1 & -1 & -2 & 4 \\ 1 & 0 & -1 & 0 & 0 \\ 0 & 1 & 0 & 1 & -2 \end{pmatrix} \underset{R_{2} \to R_{2} - R_{1}}{\smile \atop \frown} \begin{pmatrix} 1 & 1 & -1 & -2 & 4 \\ 0 & -1 & 0 & 2 & -4 \\ 0 & 1 & 0 & 1 & -2 \end{pmatrix} \underset{R_{3} \to R_{3} + R_{2}}{\smile \atop \frown} \dots
$$

$$
\dots \ \begin{pmatrix} 1 & 1 & -1 & -2 & 4 \\ 0 & -1 & 0 & 2 & -4 \\ 0 & 0 & 0 & 3 & -6 \end{pmatrix} \underset{R_{2} \to -R_{2} \atop R_{3} \to \frac{1}{3} R_{3} }{\smile \atop \frown} \begin{pmatrix} 1 & 1 & -1 & 0 & 0 \\ 0 & 1 & 0 & 0 & 0 \\ 0 & 0 & 0 & 1 & -2 \end{pmatrix} \underset{R_{2} \to R_{2} + 2 R_{3} \atop R_{1} \to R_{1} + 2 R_{3}}{\smile \atop \frown}\ \dots
$$

$$
\dots \ \underset{R_{1} \to R_{1} - R_{2}}{\smile \atop \frown} \begin{pmatrix} 1 & 0 & -1 & 0 & 0 \\ 0 & -1 & 0 & 0 & 0 \\ 0 & 0 & 0 & 1 & -2 \end{pmatrix}
$$

Il sistema associato è

$$
\begin{cases} x - z = 0 \\ y = 0 \\ t = -2 \end{cases} = \begin{cases} \begin{pmatrix} x \\ 0 \\ x \\ -2 \end{pmatrix}: x \in \mathbb{R} \end{cases}
$$
Che si può anche vedere come

$$
\begin{pmatrix} 0 \\ 0 \\ 0 \\ -2 \end{pmatrix} + \mathbb{R} \begin{pmatrix} 1 \\ 0 \\ 1 \\ 0 \end{pmatrix} = \begin{Bmatrix} \begin{pmatrix} 0 \\ 0 \\ 0 \\ -2 \end{pmatrix} + x \begin{pmatrix} 1 \\ 0 \\ 1 \\ 0 \end{pmatrix}: x \in \mathbb{R} \end{Bmatrix}
$$

Questo tra l'altro ci porta al teorema

$$
\text{Sol}(A \mid B) = x_{0} + \text{Sol}(A \mid 0)
$$

dove $x_{0}$ è la *soluzione particolare* del sistema lineare $(A \mid B)$ e $\text{Sol}(A \mid 0)$ è il [[sottospazio vettoriale]] delle soluzioni del sistema $(A \mid B)$.