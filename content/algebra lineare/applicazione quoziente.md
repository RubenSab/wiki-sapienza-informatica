---
updated_at: 2025-10-20T23:19:20.281+02:00
---
_Ricordiamo che se $X$ è un'[[teoria degli insiemi|insieme]] $\neq \emptyset$ con relazione d'equivalenza $\sim$ qualsiasi, si definisce l'[[insieme quoziente]] $\frac{X}{\sim} = \{\text{classi d'equivalenza}\} \subset \mathcal{P}(X)$._

Consideriamo $X \xrightarrow{f} Y$: sia $\sim$ la [[relazione]] d'equivalenza associata $x, x' \in X,\ x \sim x' \implies f(x) = f(x')$.

Definiamo su $\frac{X}{\sim}\times Y$ la corrispondenza $\Gamma = \{(Cl(x),\ f(x)): x \in X\}$

> **Lemma**: $\Gamma$ è il [[grafo]] di un'[[applicazione]] $\frac{X}{\sim} \xrightarrow{\overline{f}} Y$ detta **applicazione quoziente**.

Dimostrazione:

Sia $\overline{x} \in \frac{X}{\sim}$

$\overline{x} = Cl(x) \subset X$ più precisamente $\overline{x} = \{x' \in X\ \text{con}\ x' \sim x\} = \{x' \in X\ \text{con}\ f(x') = f(x)\}$ Quindi $f(\overline{x})=\{f(x'): x' \in \overline{x}\}=\{f(x)\}$

In questo modo abbiamo associato ad ogni elemento $\overline{x} \in \frac{X}{\sim}$ uno ed uno solo elemento $y=f(x) \in Y$. Questo definisce in modo univoco un'applicazione.

$$
\frac{X}{\sim} \xrightarrow{f} Y
$$

$$
\overline{f}(\overline{x})=f(x)\ \forall x \in X
$$

> N.B.: Per **costruzione**, l'applicazione è iniettiva, ed è biiettiva $\iff$ $f$ è suriettiva.

Esempio di applicazione quoziente:

- $X = \{1, 2, 3, 4, 5\}$
- $Y = \{a, b\}$

| $x$ | $f(x)$ |
| --- | ------ |
| 1   | a      |
| 2   | a      |
| 3   | b      |
| 4   | a      |
| 5   | b      |

L'insieme $\{1, 2, 4\}$ (elemento di $\frac{X}{\sim}$) è mappato ad $a$ (elemento di $Y$) e l'insieme $\{3, 5\}$ (elemento di $\frac{X}{\sim}$) è mappato a $b$ (elemento di $Y$). Questa è l'**applicazione quoziente** Notiamo che $\frac{X}{\sim} = \{Cl(1), Cl(3)\}$.

