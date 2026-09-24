---
updated_at: 2026-09-16T16:54:06.222+02:00
---
# [[scelta di k elementi da n|Scelta di k elementi da n]]

|                                    | con ripetizione                                                           | senza ripetizione                                                        |
| ---------------------------------- | ------------------------------------------------------------------------- | ------------------------------------------------------------------------ |
| scelte con ordine (disposizioni)   | [[disposizioni con ripetizioni consentite]] $$n^{k}$$                     | [[disposizioni senza ripetizioni]] $$\frac{n!}{(n-k)!}$$                 |
| scelte senza ordine (combinazioni) | [[combinazioni con ripetizioni consentite]] $$\frac{(k+n-1)!}{k!(n-1)!}$$ | [[combinazioni senza ripetizioni]] $$\binom{n}{k}= \frac{n!}{k!(n-k)!}$$ |

# Indipendenza e [[probabilità condizionata]]

- [[indipendenza di due eventi]]: $A \perp B \implies P(A \cap B) = P(A) \cdot P(B)$
- [[indipendenza di tre eventi]]: $A \perp B \perp C \implies P(A \cap B \cap C) = P(A) \cdot P(B) \cdot P(C)$
- [[probabilità condizionata]]: $P(A \mid B) = \frac{P(A \cap B)}{P(B)}$
- [[legge della probabilità totale]]: $P(A) = P(A \mid B) \cdot P(B) + P(A \mid B^c) \cdot P(B^c)$
- [[teorema di Bayes]]: $$P(A \mid B) = \frac{P(B \mid A) \cdot P(A)}{P(B \mid A) \cdot P(A) + P(B \mid A^c) \cdot P(A^c)}$$
# Distribuzioni notevoli di probabilità discreta

| Distribuzione                   | Probabilità                                 | $\mathbb{E}(X)$ |  $\text{Var}(X)$  |
| :------------------------------ | :------------------------------------------ | :-------------: | :---------------: |
| [[distribuzione di Bernoulli]]  | $\{p^x, (1-p)^{1-x}\}$ per $x \in \{0, 1\}$ |       $p$       |     $p(1-p)$      |
| [[distribuzione binomiale]]     | $p_k = \binom{n}{k} p^k (1-p)^{n-k}$        |   $n \cdot p$   | $n \cdot p(1-p)$  |
| [[distribuzione geometrica]]    | $p_k = (1-p)^{k-1} p$                       |  $\frac{1}{p}$  | $\frac{1-p}{p^2}$ |
| [[distribuzione di Poisson 🐟]] | $p_k = \frac{\lambda^k}{k!} e^{-\lambda}$   |    $\lambda$    |     $\lambda$     |

## [[serie geometriche|Serie geometrica]]
 
 $$\sum_{k=0}^{\infty} n^k = \frac{1}{1-n}$$

## [[valore atteso di una variabile aleatoria|Valore atteso]], [[varianza di una variabile aleatoria|varianza]] e [[covarianza di due variabili aleatorie|covarianza]] nel discreto
  $$\mathbb{E}(X) = \sum x \cdot P(X = x)$$
   $$X \perp Y \implies \mathbb{E}(X \cdot Y) = \mathbb{E}(X) \cdot \mathbb{E}(Y)$$

$$\text{Var}(X) = \mathbb{E}\left((X - \mathbb{E}(X))^2\right) = \sum (x - \mathbb{E}(X))^2 p_x = \mathbb{E}(X^2) - [\mathbb{E}(X)]^2$$

  > N.B.: I valori vanno al quadrato, le operazioni sono **sui valori**, non sui pesi.

  $$\text{Cov}(X, Y) = \mathbb{E}(X Y) - \mathbb{E}(X)\mathbb{E}(Y)$$
  
  $$\text{Cov}(X, Y + Z) = \text{Cov}(X, Y) + \text{Cov}(X, Z)$$
  
  $$\text{Var}(X + Y) = \text{Var}(X) + \text{Var}(Y) + 2\text{Cov}(X, Y)$$

- [[funzione generatrice dei momenti]]

$$G_X(t) = \mathbb{E}(e^{tX}) \quad \text{per } t \in (0, 1] = \sum t^x P(X = x)$$

$$G_X(t) = \mathbb{E}(e^{tX}) \implies G_X'(1) = \mathbb{E}(X)$$

> I grafici di ripartizione hanno $0$ a sinistra e il valore massimo $1$ a destra: $(P(X < x)) = F_X$

# [[probabilità continua|Probabilità continua]]

- $f(x)$ = [[funzione]] di densità di probabilità.

- Funzione di ripartizione su un intervallo $A$:
  $$F_X(x) = P(X \le x) = \int_{\text{intervallo } A} f(x) \, dx$$

- Valore Atteso:
  $$\mathbb{E}(X) = \int_{-\infty}^{+\infty} x \cdot f(x) \, dx$$

## Distribuzioni Continue Notevoli

| Distribuzione                                       | Densità di Probabilità $f(x)$                                                    |   $\mathbb{E}(X)$   |    $\text{Var}(X)$    |
| :-------------------------------------------------- | :------------------------------------------------------------------------------- | :-----------------: | :-------------------: |
| **[[legge uniforme]]**                              | $f(x) = \frac{1}{b-a} \, \mathbb{I}_{[a,b]}(x)$                                  |   $\frac{a+b}{2}$   | $\frac{(a-b)^2}{12}$  |
| **[[legge esponenziale]]**                          | $f(x) = \begin{cases} \lambda e^{-\lambda x} & x \ge 0 \\ 0 & x < 0 \end{cases}$ | $\frac{1}{\lambda}$ | $\frac{1}{\lambda^2}$ |
| **[[legge di Cauchy]]**                             | $f(x) = \frac{1}{\pi (1 + x^2)}$                                                 |                     |                       |
| **[[legge Gaussiana standard]] $N(0, 1)$**          | $f(x) = \frac{e^{-\frac{x^2}{2}}}{\sqrt{2\pi}}$                                  |         $0$         |          $1$          |
| **[[legge Gaussiana generica]] $N(\mu, \sigma^2)$** | $f(x) = \frac{e^{-\frac{(x-\mu)^2}{2\sigma^2}}}{\sqrt{2\pi \sigma^2}}$           |        $\mu$        |      $\sigma^2$       |

> N.B.: Nella gaussiana generica, $\mu$ trasla orizzontalmente e $\sigma^2$ dilata orizzontalmente e contrae verticalmente.