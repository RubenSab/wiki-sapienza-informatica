---
updated_at: 2026-01-26T12:15:28.954+01:00
---
> È l'operazione binaria che consente di selezionare le tuple dell'ipotetico [[prodotto cartesiano]] delle due [[relazione|relazioni]] che soddisfano la condizione

$$
(R_{1}.A_{1} = R_{2}.A_{1}) \land (R_{1}.A_{1} = R_{2}.A_{2}) \land \ldots \land (R_{1}.A_{k} = R_{2}.A_{k})
$$

$$
\land^{n}_{k = 1} (R_{1}.A_{k} = R_{2}.A_{k})
$$

Dove $R_{1}$ e $R_{2}$ sono i nomi delle [[relazione|relazioni]] operando e $A_{1}, A_{2}, \ldots, A_{k}$ sono attributi comuni, cioè con **lo stesso nome**, delle relazioni operando. Ciò elimina le ripetizioni degli attributi in modo **indiscriminato (!)** (può essere un problema quando nelle due relazioni ci sono attributi con lo stesso nome ma diverso significato, ad esempio l'ID di un cliente e l'ID di un'ordine).

Si denota con $r_{1} \bowtie r_{2}$.

Osservazione: $r_{1} \bowtie r_{2} = \pi_{XY}(\sigma_{C}(r_{1} \times r_{2}))$

*Esempio da [Wikipedia](https://en.wikipedia.org/wiki/Join_(relational_algebra))*

![[Pasted image 20260126120602.png]]

> N.B.: Se non ci sono attributi dello stesso nome nelle due relazioni, il join naturale è uguale al prodotto cartesiano.

> N.B.: Se le due tabelle hanno attributi con lo stesso nome, ma nessuna riga ha gli stessi valori su quegli attributi, allora non ci sono righe che soddisfano la condizione di join, quindi il join naturale è vuoto.