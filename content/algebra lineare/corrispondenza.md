---
updated_at: 2025-09-29T16:37:29.009+02:00
---
> Una corrispondenza $f=(X, Y, \Gamma)$ ($X$ = dominio, $Y$ = codominio, $\Gamma$ = grafo da $X$ a $Y$) si dice **[[applicazione]]** se $\forall a \in X,\ \exists !\ b \in Y : (a, b) \in \Gamma$ si dice che $b = f(a)$ e si scrive anche $X \xrightarrow{f} Y$ (applicazione $f$ da $X$ a $Y$).

Esempio: attraverso i diagrammi di Venn:

- $X=\{1, 2, 3\}$
- $Y=\{x, y\}$
- $f=(X, Y, \Gamma)$
- $\Gamma = \{(1, x)\}$

Questa corrispondenza non può essere un'applicazione perché non ha tutti gli elementi di $X$.

- $\Gamma = \{(1, x),(2, y),(3, y),(1, y)\}$

Questa non è una corrispondenza perché $1$ è mappato a più di un elemento.

Terminologia:

> Il codominio si chiama anche **[[teoria degli insiemi|insieme]] immagine**

> Il dominio si chiama anche **insieme di partenza**

> Sia $f : X \to Y$ un'applicazione. $\emptyset \neq X' \subseteq X$ si definisce $f(X')=\{y  \in Y : \exists x \in X'\ \text{con}\ f(x)=y\}$ si chiama l'immagine di $X'$ per $f$.

> se $X'=X$ si parla di immagine di $f$.

Esempio: insieme immagine $\subseteq$ insieme di partenza

$X' = \{1, 2\}$

$f(X') = f\{1, 2, 3\} = \{x, y\} = Y = f(X)$

$f(\{1\}) = \{x\} \iff f(1)=X$

$X'' = {2, 3} \subseteq X$

$f(X'') = \{y, y\} = \{y\}$

Esempio: inversione di una corrispondenza per trovare **l'immagine inversa**. Non si può risalire globalmente all'insieme di partenza sapendo solo la corrispondenza e il codomio, ma si può risalire a tutti gli elementi dell'insieme di partenza "collegati" al codominio.

$\Gamma = \{(1, x), (2, y), (3, y)\}$

$f^{-1}(Y)=X$

$Y'=\{x\} \implies f^{-1}(Y')=\{1\}$

$Y'' = \{y\} \implies f^{-1}(\{y\})=\{2, 3\}$