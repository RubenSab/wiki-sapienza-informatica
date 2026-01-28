---
updated_at: 2026-01-28T09:08:58.460+01:00
---
> Una *copertura minimale* di un [[insieme|insieme]] di $F$ è un insieme $G$ di [[dipendenza funzionale|dipendenze funzionali]] **[[dipendenza funzionale#^c57118|equivalente]]** a $F$ tale che:

1. per ogni dipendenza funzionale in $G$, il determinato è un singleton. (non ci sono determinati ridondanti);
2. per **nessuna** dipendenza funzionale $X \to A \in G$ esiste $X' \subset X$ tale che $G \equiv (G - \{X \to A\}) \cup \{X' \to A\}$ (nessun sottoinsieme del determinante determina il determinato: non ci sono determinanti ridondanti);
3. per nessuna dipendenza funzionale $X \to A \in G$, $G \equiv G-\{X \to A\}$ (nessuna dipendenza è ridondante).

Si chiama ***copertura*** perché è equivalente alla [[chiusura di un insieme di dipendenze funzionali|chiusura]] di $F$ e ***minimale*** perché non ha dipendenze ridondanti, secondo le tre condizioni.

Possono esserci più coperture minimali per un dato insieme di dipendenze funzionali; l'[[algoritmo]] spiegato sotto ce ne darà una per qualunque insieme di $F$, che potrebbe essere anche $F$ stesso.

1. Si applica il primo passo: **ridurre i determinati a singleton**;
2. poi il secondo a oltranza finché è possibile: **eliminare determinanti ridondanti**;
3. infine il terzo a oltranza finché è possibile: **eliminare dipendenze ridondanti**.

> N.B.: L'ordine di questi 3 passi è importante, perché ad esempio applicando per primo il terzo passo (la condizione più severa), avremmo potuto eliminare delle dipendenze che sebbene ridondanti ci avrebbero potuto aiutare a trovare altri elementi ridondanti in un passaggio intermedio.

# Esempio di applicazione dell'algoritmo

Copertura minimale di $F = \{AB \to CD, C \to E, AB \to E, ABC \to D\}$

**Primo passo**: ridurre i determinati a singleton

$$
F = \{AB \to C, AB \to D, C \to E, AB \to E, ABC \to D\}
$$

**Secondo passo**: eliminare ridondanze nei determinanti.

$AB \to C$: $A \to C$ appartiene a $F^{+}$? cioè $C$ appartiene a $(A)^{+}_{F}$? No, perché non ci sono dipendenze in cui **solo** $A$ determina un insiemi di attributi in cui è presente $C$; quindi il determinante non può essere ridotto.

Lo stesso avviene per $AB \to D$ e $AB \to E$.

$ABC \to D$: nell'insieme di dipendenze esiste $AB \to D$, quindi non solo possiamo eliminare $C$, ma anche tutta la dipendenza, che è un duplicato.

$$
F = \{AB \to C, AB \to D, C \to E, AB \to E\}
$$

**Terzo passo**: eliminare dipendenze ridondanti.

- $AB \to C$: $C$ viene determinato unicamente da $AB$, quindi la dipendenza non è ridondante.
- $AB \to D$: $D$ viene determinato unicamente da $AB$, quindi la dipendenza non è ridondante.
- $C \to E$: $(C)^{+}_{F} = \{C, E\}$, la dipendenza deve rimanere per mantenere inalterata $(C)_{F}^{+}$
- $AB \to E$: è ricavato transitivamente da $AB \to C \land C \to E$, quindi si può eliminare.

La copertura minimale è

$$
F = \{AB \to C, AB \to D, C \to E\}
$$

# Secondo esempio

$$
F = \{BC \to DE, C \to D, B \to D, E \to L, D \to A, BC \to AL\}
$$

1. Ridurre i determinati a singleton:
   $$
   F = \{BC \to D, BC \to E, C \to D, B \to D, E \to L, D \to A, BC \to A, BC \to L\}
   $$
2. Ridondanze nei determinanti:
   $$
   F = \{B \to D, BC \to E, C \to D, E \to L, D \to A, BC \to A, BC \to L\}
   $$
   A $B$ non serve $C$ per determinare $D$. Quindi $BC \to D$ diventa $B \to D$.

3. Dipendenze ridondanti:
   
   $$
   F = \{B \to D, BC \to E, C \to D, E \to L, D \to A\}
   $$
   
$BC \to L$ è stata tolta perché ottenuta per transitività ($BC \to E \land E \to L$)