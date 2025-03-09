---
updated_at: 2025-03-07T12:04:52.961+01:00
---
> Se non è possibile determinare l'asintotica di una somma usando il [[metodo della forma chiusa]] e il [[metodo dell'integrale]], allora si procede stimando lo scenario peggiore ([[notazione O-grande]]) e quello migliore ([[notazione Omega]]): se sono uguali, allora si è ricavato anche lo scenario medio ([[notazione Theta]]).

# esempio
Consideriamo la somma $\sum_{i=1}^{n}{i}$
## caso peggiore
$$\left(\sum_{i=1}^{n}{i} \leq \sum_{i=1}^{n}{n}\right) \land \left(\sum_{i=1}^{n}{n}\in O(n^{2})\right) \implies \sum_{i=1}^{n} i \in O(n^{2})$$
## caso migliore
$$\left(\sum_{i=1}^{n}{i} \geq \sum_{i=\frac{n}{2}}^{n}{i} \geq \sum_{i=\frac{n}{2}}^{n}{\frac{n}{2}} = \frac{n}{2} \sum_{i=\frac{n}{2}}^{n}{1} = \frac{n}{2}\left(n-\frac{n}{2}\right)+1 \approx \frac{n}{2}\cdot \frac{n}{2} = \frac{n^{2}}{4}\right) \land \left(\frac{n^{2}}{4}\in \Theta(n^{2})\right)\implies \sum_{i=1}^{n}{i} \in \Theta(n^{2}$$
## caso medio
$$S_{n} \in O(n^{2}) \land S_{n} \in \Omega(n^{2}) \implies S_{n} \in \Theta(n^{2})$$