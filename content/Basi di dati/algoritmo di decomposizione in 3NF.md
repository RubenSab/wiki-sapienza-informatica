---
updated_at: 2026-02-03T13:08:23.261+01:00
---
Dato uno [[tabella|schema di relazione]] e un insieme di [[dipendenza funzionale|dipendenze funzionali]] $F$ su $R$ esiste **sempre** una decomposizione $\rho = \{R_{1}, \ldots, R_{k}\}$ di $R$ che rispetta i criteri di una [[verifica di una buona decomposizione in 3NF|buona decomposizione in 3NF]], cioè:

- ogni $R_{i}$ è in [[3NF (terza forma normale)|3NF]],
- $\rho$ preserva $F$,
- $\rho$ ha un [[join naturale]] senza perdita.

Una decomposizione $\rho$ di $R$ può essere calcolata in [[complessità temporale|tempo polinomiale]] con un [[algoritmo]] che riceve in input una **qualunque** [[copertura minimale di un insieme di dipendenze|copertura minimale]] di $F$, che definiamo $G$.

**Input**: $R$, $G$.

**Output**: $\rho$.

1. $S := \emptyset$
2. for $A$ in $R$: (questa parte serve a selezionare nell'"accumulatore" $S$ tutte le dipendenze funzionali non coinvolte in nessuna dipendenza funzionale in $G$)
	1. if $A$ non è coinvolto in nessuna dipendenza funzionale in $G$:
		1. $S := S \cup \{A\}$
3. if $S \neq \emptyset$: (questa parte rimuove tutti gli attributi di $S$ da $R$, inizializzando la decomposizione $\rho$ a $S$)
	1. $R := R-S$
	2. $\rho := \rho \cup \{S\}$
4. if esiste $f \in G$ che coinvolge tutti gli attributi in $R$:
	1. $\rho := \rho \cup \{R\}$
5. else:
	1. for $X \to A$ in $G$:
		1. $\rho := \rho \cup \{XA\}$
6. **Aggiungi $\{Y\}$ a $\rho$, con $Y$ chiave di $R$ se non è già presente in nessun sottoschema di $\rho$**. Questo serve per garantire un join senza perdita.
7. (opzionale) semplifica rimuovendo tutti i sottoschemi [[sottoinsiemi]] di altri sottoschemi.

# Esempio

Dato $R = \{A, B, C, D, E, H\}$ e $F = \{AB \to CD, C \to E, AB \to E, ABC \to D\}$

> Verifica che $ABH$ è una [[chiave]] per $R$.

- $ABH$ deve determinare funzionalmente tutto lo schema:
  vero, perché la [[chiusura di un insieme di attributi|chiusura]] di $ABH$ coincide con $R$.
- Nessun sottoinsieme di $ABH$ deve determinare funzionalmente l'intero schema:
  vero, perché considerando che la chiave deve avere sicuramente $H$, $AH^{+}$ e $BH^{+}$ non coincidono con $R$.

> Sapendo che $ABH$ è l’unica chiave per $R$, verifica che $R$ non è in 3NF.

Esistono le [[dipendenza parziale|dipendenze parziali]] $AB \to CD$ e $AB \to E$, quindi $R$ non può essere in 3NF.

> Trova una copertura minimale $G$ di $F$.

Primo passo: decomporre i determinati in singleton

$$
G = \{AB \to C, AB \to D, C \to E, AB \to E, ABC \to D\}
$$

Secondo passo: rimuovere gli attributi superflui dei determinanti:

- $AB \to C$: $A_{F}^{+} = \{A\}, B_{F}^{+} = \{B\}$, quindi $C \notin A^{+}_{F}, B^{+}_{F}$. Nessun attributo è ridondante.
- $AB \to D$: $A_{F}^{+} = \{A\}, B_{F}^{+} = \{B\}$, quindi $D \notin D^{+}_{F}, B^{+}_{F}$. Nessun attributo è ridondante.
- $C \to E$: È atomica, quindi nessun attributo può essere rimosso.
- $AB \to E$: $A_{F}^{+} = \{A\}, B_{F}^{+} = \{B\}$, quindi $E \notin D^{+}_{F}, B^{+}_{F}$. Nessun attributo è ridondante.
- $ABC \to D$: $AB_{F}^{+} = \{AB, C, D, E\}, C_{F}^{+} = \{C, E\}$, quindi $D \in AB^{+}_{F}$ (perché esiste $AB \to D$ in $F$). $C$ è ridondante, quindi possiamo ridurre la dipendenza a $AB \to D$, che esiste già in $F$.

$$
G = \{AB \to C, AB \to D, C \to E, AB \to E\}
$$

Terzo passo: rimuovere le dipendenze ridondanti:

- Rimuovendo $AB \to C$ si altererebbe $AB^{+} = \{AB, C, D, E\}$, quindi la dipendenza non è ridondante.
- Rimuovendo $AB \to D$ si altererebbe $AB^{+} = \{AB, C, D, E\}$, quindi la dipendenza non è ridondante.
- Rimuovendo $C \to E$ si altererebbe $C^{+} = \{C, E\}$, quindi la dipendenza non è ridondante.
- Rimuovendo $AB \to E$ **non** si altererebbe $AB^{+} = \{AB, C, D, E\}$, quindi la dipendenza $AB \to E$ è ridondante (tra l'altro è ottenuta per transitività da $AB \to C \land C \to E$)

$$
G = \{AB \to C, AB \to D, C \to E\}
$$

> Trova una decomposizione $\rho$ di $R$ tale che preserva $G$, ogni schema in $\rho$ è in 3NF ed è senza perdita.

Iniziamo l'algoritmo: per prima cosa $H \notin G \implies \rho = \{H\}, R = \{A, B, C, D, E\}$. Non ci sono dipendenze che coinvolgono tutti gli attributi dello schema, quindi eseguiamo l'istruzione 5. dell'algoritmo, ottenendo $\rho = \{H, ABC, ABD, CE\}$.

Per avere una decomposizione con join senza perdita, aggiungiamo alla decomposizione precedente un sottoschema che contenga la chiave $ABH$ (che non è già contenuta in alcuno degli schemi ottenuti), ottenendo $\rho = \{H, ABC, ABD, CE, ABH\}$, che si semplifica in $\rho = \{ABC, ABD, CE, ABH\}$.

# Dimostrazione della correttezza dell'algoritmo

#todo pag. 5 pdf 19