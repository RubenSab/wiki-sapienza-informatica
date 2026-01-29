---
updated_at: 2026-01-29T15:24:46.283+01:00
---
# Cosa risolve l'ISAM

Quando le chiavi dei dati memorizzati in un [[database]] hanno un ordinamento naturale (come interi e stringhe), è conveniente tenerne conto nell'[[organizzazione fisica di un database relazionale|organizzazione fisica del database]]. Per più campi si può ordinare sul primo, poi il secondo e via dicendo.

Ciò è utile perché avendo una [[struttura dati]] ordinata, l'operazione di ricerca può fare uso della **[[ricerca binaria]]**, che ha [[complessità temporale]] [[notazione O-grande|logaritmica]].

# Cos'è l'ISAM

> Il file ***ISAM*** *(Indexed Sequential Access Method)* è un file i cui record sono ordinati in base alla ***chiave di ricerca***. In genere viene lasciato dello spazio libero in ogni blocco.

