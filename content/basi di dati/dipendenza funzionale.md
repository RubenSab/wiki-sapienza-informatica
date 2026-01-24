---
updated_at: 2026-01-24T16:20:48.650+01:00
---
> Una dipendenza funzionale stabilisce un particolare legame semantico tra due [[insieme|insiemi]] non vuoti di attributi $X$ e $Y$ appartenenti ad uno [[tabella#^ec7c8e|schema]] $R$.

Tale vincolo si scrive $X \to Y$ e si legge $X$ ***determina*** $Y$, cioè *se due tuple sono uguali sull'insieme di attributi $X$ allora lo sono anche sull'insieme di attributi $Y$*.

- $X$ si dice *determinante*,
- $Y$ si dice *determinato*.

Ad esempio il modello di macchina "Punto" **determina** la marca "Fiat". L'importante è che non si possa assegnare "Punto" a due marche diverse.

> In modo astratto, si può considerare la dipendenza funzionale come la coppia ordinata di [[sottoinsiemi]] di $R$, cioè $(X, Y)$.

> Chiamiamo $F$ l'insieme di tutte le dipendenze funzionali **definite esplicitamente** di uno schema di [[relazione]] soddisfatte da un'[[tabella|istanza]] per essere definita **legale**.

- [[chiusura di un insieme di dipendenze funzionali]]

# Dipendenze funzionali banali

Dati uno schema di relazione $\mathcal{R}$ e due [[insieme|sottoinsiemi]] non vuoti $X, Y \subseteq \mathcal{R}$, tali che $Y \subseteq X$ si ha che ogni istanza $r$ di $\mathcal{R}$ soddisfa la dipendenza funzionale (detta banale) $X \to Y$.

> N.B.: è **matematicamente impossibile** violare una dipendenza funzionale banale, perché ad esempio $(a_{1}, b_{1}, c_{1}) = (a_{2}, b_{2}, c_{2}) \implies (a_{1}, b_{1}) = (a_{2}, b_{2})$.

Osservazione: $X \to Y \in F^{+} \iff \forall A \in Y\ (X \to A \in F^{+})$

# Equivalenza di insiemi di dipendenze funzionali = stessa chiusura

^c57118

> Siano $F$ e $G$ due insiemi di dipendenze funzionali. $F \equiv G$ se $F^{+} = G^{+}$. Cioè $F$ e $G$ **potrebbero non contenere** le stesse dipendenze, ma le loro chiusure sì.