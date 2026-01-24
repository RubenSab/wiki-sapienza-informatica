---
updated_at: 2026-01-24T15:53:51.639+01:00
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

> Nota: Estendere la variabile $Z$ da cui prendiamo i determinanti nei cicli while successivi equivale ad applicare gli assiomi di Armstrong.

# Dimostrazione che l'[[algoritmo]] è corretto

Teorema: l'algoritmo calcola correttamente la chiusura di un insieme di attributi $X$ rispetto ad un insieme $F$ di dipendenze funzionali.

Dimostrazione:

- $Z^{(0)} :=$ valore iniziale di $Z$ ($Z^{(0)} = X$);
- $Z^{(i)},\ i \geq 1 :=$ valore di $Z$ dopo l'i-esima iterazione;
- $S^{(i)},\ i \geq 1 :=$ valore di $S$ dopo l'i-esima iterazione.

Per la natura dell'algoritmo, è evidente che $\forall i \ \ Z^{(i)} \subseteq Z^{(i+1)}$; non eliminiamo mai nessun attributo.

Scegliamo $j$ tale che $Z(j)$ sia il valore di $Z$ quando il ciclo si interrompe, terminando l'algoritmo: $S(j) \subseteq Z(j)$.

La proposizione da dimostrare diventa quindi:

$$
\boxed{A \in Z^{(j)} \iff A \in X^{+}}
$$

Cioè $Z^{j} = X^{+}$ (l'algoritmo fa effettivamente quello che dice di fare, calcolando $X^{+}$ tramite la variabile $Z$).

## Per [[induzione]], $A \in Z^{(j)} \implies A \in X^{+}$

Vogliamo dimostrare per induzione su $i$ che $\forall i \ \ Z^{(i)} \subseteq X^{+}$, quindi in particolare $Z^{(j)} \subseteq X^{+}$.
### Caso base $i = 0$

$Z^{(0)} = X \land Z \subseteq X^{+} \implies Z^{(0)} \subseteq X^{+}$

### Passo induttivo: ipotesi induttiva $Z^{(i-1)}\subseteq X^{+}$

Sia $A$ un attributo aggiunto all'i-esima iterazione, cioè $Z^{(i)} - Z^{(i-1)}$.

Sicuramente, per come è definito l'algoritmo, esiste una dipendenza $Y \to V \in F$ tale che $Y \subseteq Z^{(i-1)} \land A \in V$.

Per ipotesi induttiva, $Y \subseteq X^{+}$, quindi per il [[chiusura di un insieme di attributi#^1d8ddf|Lemma]] vale $X \to Y \in F^{A}$.

Per l'assioma della transitività $X \to Y \in F^{A} \land Y \to V \in F \implies X \to V \in F^{A}$, quindi sempre per il Lemma, $V \subseteq X^{+}$.

Dato che $A \in V$ allora $\forall A \in Z^{(i)}-Z^{(i-1)} \quad A \in X^{+}$. Da ciò segue per ipotesi induttiva che $Z^{(i)} \subseteq X^{+}$ (Gli attributi in $Z^{(i-1)}$ sono già in $X^{+}$ per ipotesi induttiva, abbiamo mostrato che ci vanno anche quelli inseriti in $Z$ all'i-esima iterazione del ciclo).

## Per dimostrazione diretta, $A \in X^{+} \implies A \in Z^{(j)}$

Sia $A \in X^{+}$. Dobbiamo dimostrare che $A \in Z^{(j)}$.

Per il Lemma vale che $X \to A \in F^{A}$ e per l'uguaglianza tra $F^{A}$ e $F^{+}$ vale che $X \to A \in F^{+}$, quindi $X \to A$ deve essere soddisfatta da **ogni** [[tabella|istanza]] legale di $R$, in particolare da $r$ definita come segue:

$$
r \ = \ \overset{Z^{(j)}}{\overbrace{\begin{matrix} 1 & 1 & \dots & 1 \\ 1 & 1 & \dots & 1 \end{matrix}}} \quad \overset{R - Z^{(j)}}{\overbrace{\begin{matrix} 1 & 1 & \dots & 1 \\ 0 & 0 & \dots & 0 \end{matrix}}}
$$

## $r$ è un'istanza legale di $R$

$r$ è un'istanza legale se soddisfa **ogni** $V \to W \in F$:

- se $V \not\subset Z^{(j)}$, allora le due tuple sono diverse su $V$ perché c'è almeno un attributo di $V$ contenuto in $R-Z^{(j)}$, quindi la dipendenza è soddisfatta.
- se $V \subseteq Z^{(j)}$ i valori delle due tuple sono uguali. Se le due tuple avessero valori diversi su $W$ (e quindi se la dipendenza non fosse soddisfatta), si avrebbe $S^{(j)} \not\subset Z^{(j)}$ e quindi $Z^{(j)}$ non sarebbe **il valore finale di $Z$**.
  Questo perché se $V \subseteq Z^{(j)}$ e $W$ avesse degli attributi in $R-Z^{(j)}$ allora l'algoritmo non sarebbe ancora finito, perché questi attributi si potrebbero ancora raccogliere in $Z^{(j+1)}$: ciò vorrebbe dire che $Z^{(j)}$ non è il valore finale di $Z$, ma ciò è un **assurdo** in contraddizione con la costruzione dell'istanza $r$.

Abbiamo dimostrato che $r$ è un'istanza legale di $R$.

### Considerazione finale

Dato che $r$ è legale, deve soddisfare $X \to A \in F^{+}$.

Per costruzione, ovviamente esistono due **tuple uguali su $X$** (perché $X = Z^{(0)} \subseteq Z^{(j)}$, parte a destra dello schema con tutti 1): dato che le due tuple sono uguali su tutti gli attributi in $Z^{(j)}$, allora devono essere uguali anche su $A \in X$, quindi $A \in Z^{(j)}$.

$$
(A \in Z^{(j)} \implies A \in X^{+}\ \land \ A \in X^{+} \implies A \in Z^{(j)}) \implies \boxed{A \in Z^{(j)} \iff A \in X^{+}}
$$

$\square$