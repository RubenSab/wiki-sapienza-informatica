---
updated_at: 2025-05-18T19:19:56.441+02:00
---
# Per le [[ottimizzazione delle reti combinatorie|reti]]

> La **complessità** di una rete combinatoria è proporzionale al numero di porte (che anche dipende dal numero di ingressi (**fan-in**) in ogni porta, se il circuito è dotato di porte a più ingressi) e al tempo di attraversamento del circuito.

le [[reti AND-TO-OR]] ( o [[reti OR-TO-AND|OR-TO-AND]]) sono minimali se tra tutte le reti possibili AND-TO-OR (o OR-TO-AND) ha:
- il minimo numero di porte AND (o OR)
- il minimo numero di ingressi per ogni porta
# Per le [[espressioni booleane]]

Un'espressione SOP (o POS) è minimale se tra tutte le espressioni booleane possibili SOP (o POS) ha:
- Il minimo numero di prodotti (o somme)
- il minimo numero di letterali per ogni prodotto (o somma)

# Per gli [[automa a stati finiti (finite state automata)|automi a stati finiti]]

Un'automa è minimale se è realizzato con il minor numero di [[flip-flop]] possibili, cioè non ha stati equivalenti.

> Due stati si dicono equivalenti se per ogni possibile valore di ingresso transitano nello stesso stato successivo e producono la stessa uscita.