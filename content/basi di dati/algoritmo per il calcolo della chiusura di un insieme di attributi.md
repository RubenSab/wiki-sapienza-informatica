---
updated_at: 2025-11-23T10:53:53.685+01:00
---
> È migliore dell'applicazione indiscriminata degli [[chiusura di Armstrong|assiomi di Armstrong]] per calcolare $X^{+}$, ha complessità polinomiale.

**Input**: una [[tabella|schema di relazione]] $R$, un insieme $F$ di [[dipendenza funzionale|dipendenze funzionali]] su $R$, un [[sottoinsiemi|sottoinsieme]] $X$ di $R$.

**Output**: la [[chiusura di un insieme di attributi|chiusura]] di $X$ rispetto ad $F$ (restituita nella variabile $Z$)

1. $Z:=X$
   Inizialmente assegniamo $X$ stesso all'accumulatore di $X^{+}$ che useremo nel ciclo.
2. $S:=\{A\ \text{tale che}\ Y \to V \in F \quad \land \quad A \in V \quad \land \quad Y \subseteq Z\}$
   Scegliamo $A$ in modo che sia determinata da un insieme di attributi appartenenti alla chiusura di $X$ come calcolata fino a questo momento; poi assegniamola a $S$.
3. `while` $S \not\subset Z$:
   Fermiamoci quando non si può scegliere un attributo $S$ in modo che non sia già nella chiusura di $X$.
	1. $Z:= Z\cup S$
	   Aggiungiamo $S$ alla chiusura di $X$.
	2. $S := \{A\ \text{tale che}\ Y \to V \in F \quad \land \quad A \in V \quad \land \quad Y \subseteq Z\}$
4. `return` $Z$

## Dimostrazione che l'algoritmo è corretto

#todo pag. 9 del pdf 11