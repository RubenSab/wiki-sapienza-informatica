---
updated_at: 2025-10-07T16:36:12.012+02:00
---
> È l'operazione unaria che consiste di selezionare sono alcuni attributi (colonne) della [[tabella]] ([[relazione]] in input).

Si denota con il simbolo $\pi$ e gli attributi selezionati vanno al pedice. È seguito dal nome dello [[tabella#^ec7c8e|schema]] tra parentesi tonde.

$$
\pi_{A1,\ A2,\ \ldots, A_{k}}(r)
$$

Esempio: ritornare una tabella con nome e codice fiscale degli impiegati di un'azienda.

$$
\pi_{\text{nome},\ \text{codice fiscale}}(\text{Impiegati})
$$

> N.B.: La proiezione può diminuire la [[cardinalità]] della [[relazione]] di partenza, perché i duplicati possono venire collassati.