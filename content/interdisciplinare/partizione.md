---
updated_at: 2025-10-01T12:01:35.198+02:00
---
> Una partizione di un [[teoria degli insiemi|insieme]] $X$ è una famiglia $\mathcal{P}$ di [[sottoinsiemi|sottoinsiemi]] di $X$ tale che:

1. Gli insiemi della partizione non contengono l'insieme vuoto: $\forall P \in \mathcal{P}\ (P\neq \emptyset)$;
2. Gli insiemi della partizione sono due a due **disgiunti** $\forall P, Q \in \mathcal{P}\ (P\neq Q \implies P \cap Q = \emptyset)$;
3. Ogni elemento di $X$ appartiene a un insieme della partizione: $\forall x \in X\ (\exists P : x \in P)$.

Esempio: L'insieme i cui elementi sono le [[classe di equivalenza|classi di equivalenza]] secondo la [[relazione]] di congruenza modulo 2 è una partizione di $\mathbb{Z}$.

> Più generalmente data una relazione d'equivalenza $\mathcal{R}=(X, \Gamma)$, l'insieme $\mathcal{R}=\{Cl(x) : x \in X\}$ è una partizione di $X$.

Ciò mette in evidenza la corrispondenza tra partizioni e classi di equivalenza.

---

> **Proposizione 1**: A ogni partizione corrisponde una relazione di equivalenza.

$$
\{\mathcal{R} : \text{relazione di equivalenza su}\ X\} \to \{\mathcal{P}\ \text{partizione di}\ X\}
$$

$$
\mathcal{R} = \mathcal{P} = \{Cl(x) : x \in X\}
$$

Viceversa, sia $\mathcal{P}$ una partizione di $X$. Definiamo una relazione $\mathcal{R}$ su $X$ nel modo seguente:

$$
x, y \in X\ \ \ x\ \mathcal{R}\ y \iff \exists\ p \in \mathcal{P} : x, y \in P
$$

"Due elementi $x$ e $y$ di $X$ sono in relazione $\mathcal{R}$ se e solo se esiste un insieme $P$ nella famiglia $\mathcal{P}$ tale che sia $x$ che $y$ appartengono a $P$."

---

> **Proposizione 2**: La relazione su $X$ definita in questo modo è una relazione d'equivalenza.

Per dimostrare la proposizione 2, la relazione deve essere riflessiva(1), simmetrica(2), transitiva(3).

1. Sia $x \in X$. $\mathcal{P}$ partiziona allora $\exists P \in \mathcal{P} : x  \in P \implies x\ \mathcal{R}\ x$.
2. Sia $x\ \mathcal{R}\ y \iff \exists P \in \mathcal{P}$ con $x, y \in P$, quindi anche con $y, x \in P \implies y\ \mathcal{R}\ x$ (possiamo invertire $x\ \mathcal{R}\ y$ e ricavare $x\ \mathcal{R}\ y$ sia grazie alla proposizione 1 che alla [[classe di equivalenza#^517e46|proprietà di caratterizzazione della classe di equivalenza]], infatti se $x$ è in relazione con $y$, vuol dire che sono nella stessa classe di equivalenza, quindi nello stesso insieme $P$ della partizione $\mathcal{P}$).
3. Siano $x, y, z \in X$ tali che $x\ \mathcal{R}\ y$ e $y\ \mathcal{R}\ z$. Per la proposizione 1: $x\ \mathcal{R}\ y \implies \exists\ P_1 \in \mathcal{P} : x, y \in P_1$ e $y\ \mathcal{R}\ z \implies \exists\ P_2 \in \mathcal{P} : y, z \in P_2$. Poiché $\mathcal{P}$ è una partizione, gli insiemi $P_1$ e $P_2$ sono disgiunti o coincidenti. Ma $y \in P_1$ e $y \in P_2$, cioè hanno un'intersezione e per essere insiemi validi all'interno della partizione, vale che $P_1 = P_2$. Ne consegue che $x, y, z \in P_1$, e quindi $x, z \in P_1$, pertanto $x\ \mathcal{R}\ z$.
