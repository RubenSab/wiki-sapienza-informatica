---
updated_at: 2026-01-23T13:17:31.429+01:00
---
> Una [[tabella]] è detta *master* se contiene solo le informazioni principali che **controllano** una o più tabelle *slave*, le quali ne espandono i dettagli.

Esempio:

- Ordini = (IdOrdine, Cliente, Data)
- MerceOrdine = (IdOrdine, Prodotto, Quantità)

> Come di norma, la tabella MerceOrdine si lega alla tabella Ordini con la [[foreign key]] IdOrdine dello schema Ordini.