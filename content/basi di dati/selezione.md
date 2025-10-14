---
updated_at: 2025-10-07T17:14:18.719+02:00
---
> È l'operazione unaria che consente di selezionare sono le tuple (righe) della [[tabella]] ([[relazione]] in input) che soddisfano una data condizione.

Si denota con il simbolo $\sigma$ e l'insieme di condizioni $C$ va al pedice. È seguito dal nome dello [[tabella#^ec7c8e|schema]] tra parentesi tonde.

$$
\sigma_{C}(r)
$$

La condizione è un'[[espressioni booleane|espressione booleana]] composta dalle espressioni atomiche:

- $A\ \Theta\ B$
- $A\ \Theta\ C$

Dove $\Theta$ è un operatore di confronto, $A$ e $B$ sono due attributi dello stesso dominio e **della stessa tupla** e $C$ è una costante dello stesso dominio di $A$.

Esempio: selezionare sono i clienti residenti a Roma nati dopo il 2000.

$$
\Theta_{\text{Città='Roma'}\ \land\ \text{Nascita>2000}}(\text{Cliente})
$$

> N.B.: La selezione non comporta la perdita di duplicati come la [[proiezione]].