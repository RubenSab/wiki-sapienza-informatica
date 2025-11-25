---
updated_at: 2025-11-25T17:14:40.893+01:00
---
> Una *copertura minimale* di un [[teoria degli insiemi|insieme]] di $F$ è un insieme $G$ di [[dipendenza funzionale|dipendenze funzionali]] **[[dipendenza funzionale#^c57118|equivalente]]** a $F$ tale che:

1. per ogni dipendenza funzionale in $G$, il determinato è un singleton. (non ci sono determinati ridondanti);
2. per nessuna dipendenza funzionale $X \to A \in G$ esiste $X' \subset X$ tale che $G \equiv (G - \{X \to A\}) \cup \{X' \to A\}$ (non ci sono determinanti ridondanti);
3. per nessuna dipendenza funzionale $X \to A \in G$, $G \equiv G-\{X \to A\}$ (nessuna dipendenza è ridondante).

Si chiama copertura perché è uguale alla chiusura di $F$ e minimale perché non ha dipendenze ridondanti, secondo le tre condizioni.

Possono esserci più coperture minimali per un dato insieme di dipendenze funzionali; l'algoritmo ce ne darà una per qualunque insieme di $F$, che potrebbe essere anche $F$ stesso.

Si applica il primo passo, poi il secondo a oltranza finché è possibile, poi il terzo a oltranza.

> N.B.: L'ordine di questi 3 passi è importante, perché ad esempio applicando per primo il terzo passo (la condizione più severa), avremmo potuto eliminare delle dipendenze che sebbene ridondanti ci avrebbero potuto aiutare a trovare altri elementi ridondanti.

Esempio: $F = \{AB \to C, A \to D, D \to C\}$

#todo pag 15 pdf 17