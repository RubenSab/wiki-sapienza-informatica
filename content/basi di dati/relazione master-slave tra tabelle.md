---
updated_at: 2025-11-11T23:56:07.151+01:00
---
> Una [[tabella]] è detta *master* se contiene solo le informazioni principali, che controllano una o più tabelle *slave*, le quali ne espandono i dettagli.

Esempio:

- Ordini = (IdOrdine, Cliente, Data)
- MerceOrdine = (IdOrdine, Prodotto, Quantità)

> Come di norma, la tabella MerceOrdine si lega alla tabella Ordini con la [[foreign key]] IdOrdine.