---
updated_at: 2025-11-23T11:39:19.101+01:00
---
> Si può usare l'[[algoritmo per il calcolo della chiusura di un insieme di attributi]] per determinare le [[chiave|chiavi]] di uno [[tabella|schema]] $R$ su cui è definito un [[teoria degli insiemi|insieme]] di [[dipendenza funzionale|dipendenze funzionali]] $F$.

Si parte da un insieme di attributi $X$ che si sospetta essere una chiave e si calcola la sua chiusura con l'algoritmo.

La condizione **necessaria** per cui $X$ è una chiave è che esso determini tutto $R$. Quindi se il risultato dell'algoritmo non è $R$, esso non può essere una chiave.

Poi va controllato (sempre con l'algoritmo della chiusura) anche che non esiste **nessun** sottoinsieme proprio di $X$ che determina tutto $R$.

Osservazioni:

- Conviene partire dai sottoinsiemi di $X$ con cardinalità maggiore, oppure meglio dagli insiemi $X = R-(W-V)$ con $V \to W \in F$.
- Gli attributi che non sono determinati da nessuna dipendenza funzionale (non compaiono mai a destra) sono **sicuramente** in ogni chiave.
- Uno schema può avere più chiavi.

# Test di unicità della chiave

1. Si calcola l'intersezione tra tutti gli insiemi $X = R-(W-V)$ con $V \to W \in F$ (scelta una alla volta per ogni insieme calcolato);
2. Si calcola la chiusura del risultato;
3. Se la chiusura determina tutto $R$ esiste una sola chiave, **altrimenti** ne esistono di più e vanno trovate tutte.

# Test  per la [[3NF (terza forma normale)]]

1. Iniziamo calcolando le chiusure dei determinanti delle dipendenze funzionali per verificare che non sono superchiavi (la loro chiusura è $R$ e non contengono chiavi)
2. Se nessuna è una superchiave, aggiungiamo a ognuna gli attributi che **sicuramente** fanno parte della chiave, cioè quelli che **non compaiono in nessuna dipendenza funzionale** oppure **non compaiono mai a destra** (non sono determinati da nessuna dipendenza funzionale)

Oppure, trovata la chiave di uno schema, se si trova anche una sola [[dipendenza parziale]] o [[dipendenza transitiva|transitiva]], allora lo schema non è in 3NF.