---
updated_at: 2025-12-15T14:02:31.651+01:00
---
> La *legge esponenziale di parametro $\lambda$ di [[probabilità continua]]* è definita tramite la [[variabile aleatoria indicatrice]]:

$$
f(x) = \lambda e^{-\lambda x} \cdot \mathbb{1}_{[0, +\infty)}(x) = \begin{cases} \lambda e^{-\lambda x} & x \geq 0 \\ 0 & x < 0 \end{cases}
$$

è l'"analogo" (continuo) della [[distribuzione geometrica]] (discreta).

# [[funzione generatrice dei momenti|Funzione generatrice dei momenti]]

$$
M_{X}(\vartheta) = \mathbb{E}(e^{\vartheta X}) = \int_{-\infty}^{\infty} e^{\vartheta x} f(x)\ dx = \int_{-\infty}^{\infty} e^{-\lambda x} \cdot \mathbb{1}_{[0, +\infty)}(x)\ dx = \int_{-\infty}^{\infty} \lambda e^{(\vartheta - \lambda) x}\ dx = \lambda \int_{0}^{\infty} e^{(\vartheta-\lambda) x}\ dx
$$

$$
M_{X}(\vartheta) = \begin{cases} \frac{\lambda}{\lambda - \vartheta} & \text{se}\ \vartheta < \lambda \\ +\infty & \text{altrimenti} \end{cases}
$$

# [[valore atteso di una variabile aleatoria|Valore atteso]]

Deriviamo $M_{X}(\vartheta)$, ottenendo $\mathbb{E}(X)$ e $\mathbb{E}(X^{2})$.

Per $\vartheta < \lambda$:

$$
M'_{X}(\vartheta) = \frac{d}{d \vartheta} \left(\frac{\lambda}{\lambda - \vartheta}\right) = + \frac{\lambda}{(\lambda - \vartheta)^{2}} \to M'_{X}(0) = \mathbb{E}(X) = \frac{1}{\lambda}
$$

$$
M''_{X}(\vartheta) = \frac{+2\lambda}{(\lambda - \vartheta)^{3}} \to M''_{X}(0) = \mathbb{E}(X^{2}) = \frac{2}{\lambda^{2}}
$$

# [[varianza di una variabile aleatoria|Varianza]]

Usiamo i valori calcolati nel passaggio precedente:

$$
\text{Var}(x) = \mathbb{E}(X^{2}) - (\mathbb{E}(X))^{2} = \frac{2}{\lambda^{2}} - (\frac{1}{\lambda})^{2} = \frac{1}{\vartheta^{2}}
$$