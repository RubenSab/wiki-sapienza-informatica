---
updated_at: 2025-12-01T14:37:48.174+01:00
---
> Osserviamo $n$ lanci ripetuti di una moneta truccata, ma non conosciamo $p$ (la probabilità di testa). Vogliamo usare le osservazioni dell'esperimento per *stimare* $p$. Abbiamo *tolleranza* per un errore dell'1%. Quante osservazioni ci servono (quanto deve essere grande $n$) per stimare $p$ entro la soglia di tolleranza?

Stimiamo $p$ con la proporzione di teste $\overline{X} = \frac{1}{n} \sum_{k = 1}^{n} X_{K}$.

Chiediamo quanto deve essere grande $n$ per essere sicuri che

$$
\mathbb{P}(|\overline{X} - p| \geq 0.01) \leq \varepsilon
$$

- $\overline{X}$ è la stima di $p$
- $\varepsilon$ è la probabilità di errore (umano) dell'esperimento

Per la [[disuguaglianza di Ghebyshev]] sappiamo che

$$
\mathbb{P}(|\overline{X} - p| \geq 0.01) \leq \frac{p(1-p)}{n(0.01)^{2}} \leq \varepsilon
$$

Come ci assicuriamo che $n$ sia abbastanza grande tale che

$$
\frac{p(1-p)}{n(0.01)^{2}} \leq \varepsilon \quad \forall p \in (0,1)\ ?
$$

Basta considerare il worst case scenario, richiedendo che

$$
\max_{p \in (0,1)} \left(\frac {p(1-p)}{n (0.01)^{2}}\right) \leq \varepsilon
$$

con $p=\frac{1}{2}$, cioè che

$$
\frac{1}{4n(0.01)^{2}} \leq \varepsilon\ \to\ n \geq \frac{1}{4 \varepsilon (0.01)^{2}}
$$