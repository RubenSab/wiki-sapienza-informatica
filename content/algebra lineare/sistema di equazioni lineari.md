---
updated_at: 2026-01-13T23:52:02.526+01:00
---
> Dato un [[campo]] $K$, un *sistema lineare* di $M$ equazioni e $n$ indeterminate a coefficienti in $K$, è un sistema di equazioni del tipo:

$$
* = \begin{cases}
a_{11}x_{1} + a_{12} + \dots + a_{1n} x_{n} = b_{1} \\
a_{21}x_{1} + a_{22} + \dots + a_{2n} x_{n} = b_{2} \\
\dots \\
a_{M1}x_{1} + a_{M2} + \dots + a_{Mn} x_{n} = b_{M} \\
\end{cases}
$$

Dove $b_{ij}$ sono **termini costanti** e $x_{j}$ le **indeterminate**.

# Notazione compatta con le [[spazio vettoriale di matrici|matrici]]

Siano le matrici:

$$
A = (a_{ij})_{1 \leq j \leq m,\ 1 \leq j \leq n} \in \mathcal{M}_{m, n}(K) \quad X := \begin{pmatrix} x_{1} \\ \vdots \\ x_{n} \end{pmatrix} \in \mathcal{M}_{m, n}(K) \quad B := \begin{pmatrix} b_{1} \\ \vdots \\ b_{M} \end{pmatrix} \in \mathcal{M}_{m, n}(K)
$$

- $A$ = matrice dei coefficienti dei polinomi
- $X$ = matrice colonna delle indeterminate
- $B$ = matrice colonna delle costanti a destra dell'uguale

Il sistema $*$ si scrive:

$$
AX = B
$$

$$
A X = \begin{pmatrix} A_{1} \\ \vdots \\ A_{M} \end{pmatrix} \quad X = \begin{pmatrix} \langle A_{1}, X \rangle \\ \vdots \\ \langle A_{M}, X \rangle \end{pmatrix}
$$

## Esempio 1

$$
\begin{cases}
2x_{1} + x_{2} - 3x_{3} + x_{4} = 1 \\
x_{3}+ x_{4} = 5 \\
x_{1} - x_{2} - x_{3} - 2x_{4} = 0
\end{cases}
$$

$$
B = \begin{pmatrix} 1  \\ 5 \\ 0 \end{pmatrix} \quad X = \begin{pmatrix} x_{1} \\ x_{2} \\ x_{3} \\ x_{4} \end{pmatrix} \quad A \in \mathcal{M}_{3,4}(\mathbb{R})
$$

$$
A = \begin{pmatrix} 2 & 1 & -3 & 1 \\ 0 & 0 & 1 & 1 \\ 1 & -1 & -1 & -2 \end{pmatrix}
$$

## Esempio 2

$A \in GL_{n}(K)$ su $B = K^{n}$

$(\square)\ AX = B \quad X = \begin{pmatrix} x_{1} \\ \vdots \\ x_{n} \end{pmatrix}$

Claim: $\text{Sol}(\square)$ è un singleton.

1. $A$ è una matrice quadrata: $A \in GL_{n}(K) = \mathcal{M}_{n,n}(K) \implies \exists A^{-1} \in GL_{n}(K)$ unicamente determinata, tale che $A^{-1} A = A A^{-1} = I_{n}$ (abbiamo usato il fatto che le matrici quadrate sono invertibili).
2. Consideriamo $AX = B$. Moltiplichiamo a sinistra per $A^{-1}$, quindi $A^{-1} A X = A^{-1} B \to X = A^{-1} B$.
3. $\text{Sol}(\square) = \{A^{-1} X\}$.

# Risoluzione dei sistemi

> *Risolvere* un sistema lineare vuol dire "descrivere" l'[[insieme]] delle sue soluzioni

$$
\text{Sol}(*) = \left\{ \begin{pmatrix} x_{1} \\ \vdots \\ x_{n}\end{pmatrix} \in K^{n}: *\ \text{è verificato} \right\}
$$

> Se $\text{Sol}(*) = \emptyset$ allora si dice che il sistema è *incompatibile* o impossibile; in caso contrario si dice *compatibile*. Ad esempio $\begin{cases} x_{1} = 0 \\ x_{1} = 1 \end{cases}$ è incompatibile.

#todo separa in due note differenti
## Metodo di Gauss

Consideriamo un sistema lineare $(*) \quad AX = B$.

> Chiamiamo *matrice completa* $(A \mid B) \in \mathcal{M}_{m, n+1}$ #todo esempio

Ricordiamo che risolvere $*$ equivale a trovare tutti gli $X \in \mathcal{M}_{n,1}(K)$ con $AX = B$.

### Definizioni preliminari all'algoritmo

#todo rispiega da [wikipedia](https://en.wikipedia.org/wiki/Matrix_(mathematics)#cite_note-FOOTNOTELang1986[httpbooksgooglecombooksidc_NEBAAAQBAJpgPA71_71]-31)
#### Operazioni elementari lecite sulle righe della matrice completa ($A \mid B$)

- Permutare righe;
- Sostituire una riga con un suo multiplo scalare non nullo $r \mapsto \lambda r$ con $\lambda \in K^{X}$;
- Sostituire una riga con la stessa più un multiplo scalare di un altra $r \mapsto r + \lambda r'$;

#### Convenzioni di notazione

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

#### Teorema di Gauss

- In ogni classe di $\smile \atop \frown$ di matrici complete $(A \mid B)$ esiste un'unica matrice a gradini ridotta.
- $(A \mid B)\ {\smile \atop \frown}\ (A' \mid B') \implies (A \mid B) \sim (A' \mid B')$.

>N.B.: Contro-intuitivamente, l'[[algoritmo]] di Gauss è la dimostrazione di questo teorema, non il contrario.

### Esercizi

#### 1.

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