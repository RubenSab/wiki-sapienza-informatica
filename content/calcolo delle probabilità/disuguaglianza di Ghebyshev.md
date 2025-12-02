---
updated_at: 2025-12-01T14:10:45.387+01:00
---
> Sia $X$ una [[variabili aleatorie|variabile aleatoria]] con [[valore atteso di una variabile aleatoria|media]] $\mathbb{E}(X)$ e [[varianza di una variabile aleatoria|varianza]] $\text{Var}(X)$. Allora $\forall \lambda > 0$

$$
\mathbb{P}(| X - \mathbb{E}(X) | \geq \lambda) \leq \frac{\text{Var}(X)}{\lambda^{2}}
$$

# Dimostrazione: come ricavarla dalla [[disuguaglianza di Markov]]

$$
\mathbb{P}(| X - \mathbb{E}(X) | \geq \lambda) = \mathbb{P}((X - \mathbb{E}(X))^{2} \geq \lambda^{2})
$$

Cambio di variabile $(X - \mathbb{E}(X))^{2} = Y$

$$
\mathbb{P}(Y \geq \lambda^{2}) \underset{\text{Markov}}{\leq} \frac{\mathbb{E}(Y)}{\lambda^{2}} = \frac{\mathbb{E}((X - \mathbb{E}(X))^{2})}{\lambda^{2}} = \frac{\text{Var}(X)}{\lambda^{2}}
$$

# Esempio con lanci ripetuti di moneta

Lancio ripetutamente una moneta con probabilità di testa $p \in (0, 1)$.

Definiamo la [[variabile aleatoria indicatrice]] $X_{K} = \mathbb{1}(T\ \text{al lancio}\ K),\ k \geq 1$.

Allora le $X_{K}$ sono variabili [[indipendenza di n eventi|indipendenti]] $\text{Bernoulli}(p)$.

Sia la media campionaria

$$
\overline{X} = \frac{1}{n} \cdot \sum_{k = 1}^{n}X_{K} = \frac{\text{numero di T nei primi n lanci}}{n} = \text{proporzioni di T nei primi n lanci}
$$

>N.B.: La varianza decresce all'aumentare del numero di lanci.

## Caso particolare, moneta equa ($p = \frac{1}{2}$)

In questo caso

$$
\mathbb{E}(\overline{X}) = p = \frac{1}{2}, \quad \text{Var}(\overline{X}) = \frac{p(1-p)}{n} = \frac{1}{4n}
$$

Mettiamo $\lambda = 0.1$

$$
\mathbb{P}\left(|\overline{X} - \frac{1}{2}| \geq 0.1\right) \leq \frac{{\text{Var}(\overline{X})}}{(0.1)^{2}} = \frac{\frac{1}{4n}}{(0.1)^{2}} = \frac{1}{n} \cdot \frac{1}{4 \cdot 0.01} \quad (\lim_{n \to 0}=0 )
$$

Più lanci faccio, più è meno probabile che la proporzione tra teste e croci **sia lontana** da $\frac{1}{2}$ (la varianza tende a 0).