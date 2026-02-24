---
updated_at: 2025-04-10T13:13:36.661+02:00
---
> Consiste nel rappresentare graficamente come un albero l'evoluzione delle chiamate ricorsive fermandosi a un livello arbitrario, calcolare il costo totale di ogni livello e poi sommare i costi totali di ogni livello, fermandosi quando si raggiunge il caso base.

Esempio:

$$T(n) =
\begin{cases}
\Theta(1) & \text{se } n=1 \\
2T(\frac{n}{2}) + \Theta(n) & \text{altrimenti}
\end{cases}
$$

Ogni sotto-problema $T(\ldots)$ costa come parte di complessità non ricorsiva del caso ricorsivo, in questo caso $\Theta(n)$.

$$T(n) = \Theta(n) \to
\begin{cases}
T\left(\frac{n}{2}\right) = \Theta\left(\frac{n}{2}\right) \to \begin{cases} T\left(\frac{n}{4}\right) = \Theta(\frac{n}{4})  \\ T\left(\frac{n}{4}\right) = \Theta(\frac{n}{4}) \end{cases} \\
T\left(\frac{n}{2}\right) = \Theta\left(\frac{n}{2}\right) \to \begin{cases}T\left(\frac{n}{4}\right) = \Theta(\frac{n}{4}) \\ T\left(\frac{n}{4}\right) = \Theta(\frac{n}{4}) \end{cases}
\end{cases}
$$

Il primo livello costa $\Theta(n)$, anche il secondo, il terzo e così via; quindi il livello $k$ costerà $\Theta(n)$.

Ora calcoliamo quando l'algoritmo si fermerà, cioè quando raggiungerà il caso base.
- Raggiungere il livello con i casi base significa ritrovarsi con $T(\text{caso base})$ a un certo punto dell'albero, in questo caso $T(1)$.
- Si può vedere che il sotto-problema al livello generico $k$ è nella forma $T(\frac{n}{2^{k}})$.
- Quindi $T(1)$ si raggiungerà quando $\frac{n}{2^{k}}=1$, cioè quando $k \approx \log_{2}{n}$.

Abbiamo ottenuto che servono $\log_{2}{n}$ livelli per arrivare al caso base $T(1)$. Sommiamo quindi tutti i livelli:
$$T(n) = \sum_{k=0}^{\log_{2}{n}}{\Theta(n)}=\Theta(n \cdot \log{n})$$