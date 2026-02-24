---
updated_at: 2025-03-27T13:52:55.185+01:00
---
> Il binding consiste nell'associare un [[metodo]] con il [[tipi|tipo]] della [[classe]] di una [[variabile]] riferimento. 
# Binding statico e dinamico

> Il binding **statico** avviene **prima dell'esecuzione**.

> Il binding **dinamico** avviene durante l'esecuzione (a **run-time**). È implementato dal [[polimorfismo]].

Esempio: se la classe B estende la classe A, e nel codice di B scriviamo `super.metodo()`, allora grazie al binding dinamico `super` si riferirà ad A.