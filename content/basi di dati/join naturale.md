---
updated_at: 2025-11-11T16:28:11.768+01:00
---
> È l'operazione binaria che consente di selezionare le tuple dell'ipotetico [[prodotto cartesiano]] dei due operandi che soddisfano la condizione

$$
(R_{1}.A_{1} = R_{2}.A_{1}) \land (R_{1}.A_{1} = R_{2}.A_{2}) \land \ldots \land (R_{1}.A_{k} = R_{2}.A_{k})
$$

$$
\land^{n}_{k = 1} (R_{1}.A_{k} = R_{2}.A_{k})
$$

Dove $R_{1}$ e $R_{2}$ sono i nomi delle [[relazione|relazioni]] operando e $A_{1}, A_{2}, \ldots, A_{k}$ sono attributi comuni, cioè con **lo stesso nome**, delle relazioni operando. Ciò elimina le ripetizioni degli attributi in modo **indiscriminato (!)** (può essere un problema quando nelle due relazioni ci sono attributi con lo stesso nome ma diverso significato, ad esempio l'ID di un cliente e l'ID di un'ordine).

Si denota con $r_{1} \triangleright \triangleleft\ r_{2}$.

Osservazione: $r_{1} \triangleright \triangleleft\ r_{2} = \pi_{XY}(\sigma_{C}(r_{1} \times r_{2}))$

> N.B.: Se non ci sono attributi dello stesso nome nelle due relazioni, il join naturale è uguale al prodotto cartesiano.

> N.B.: Quando non ho attributi con stesso valore e stesso nome, il join naturale è vuoto.