---
updated_at: 2026-10-30T18:17:45.524+01:00
---
> Una [[grammatica acontestuale (CFG)]] è in **forma normale** se oni sua regola è nella forma $A \to BC$ oppure $A \to a$. Dove $A, B, C \in V,\quad a \in \Sigma,\quad B,C \notin S$. È ammessa anche la regola $S \to \varepsilon$.

> Teorema: ogni CFG ammette una CFG equivalente nella forma normale di Chomsky.

Per farlo, dobbiamo trasformare le regola della CFG:

1. Per prima cosa aggiungo $S_{0}$, la *nuova variabile iniziale*, e con essa la regola $S_{0} \to S$.
2. Passiamo poi alle *$\varepsilon$-regole ($A \to \varepsilon$) in cui la variabile a sinistra appare nella destra di un'altra regola ($\ldots \to A$)*. Per ogni occorrenza di $A$ sul lato destro di una regola, aggiungo nuove regole con occorrenza cancellata. (praticamente per poter togliere $A \to \varepsilon$ si applica $A \to \varepsilon$ a tutte le regole vecchie).
   **Esempio**:
   $A \to \varepsilon$
   $B \to u A v$, con $u, v$ stringhe di variabili/terminali.
   $\implies B \to uv$
   **Altro esempio**:
   $B \to u A v A w$
   $\implies B \to u v w \mid u A v w \mid u v A w \mid u A v A w$
   **Altro esempio**:
   $B \to C \quad C \to A \mid c$ diventano $B \to A \mid c$ e $C \to A \mid c$
3. Togliamo le *regole unitarie*: $A \to B$. Per ogni occorrenza di regole $B \to u$, aggiungo $A \to u$. ($u$ sempre sequenza di variabili/terminali)
   ![[subway-surfers.gif]]
   *(piccola gif a scopo di intrattenimento)*
4. Infine tolgo tutte le *regole che non hanno esclusivamente 2 variabili a destra*:
   $A \to V_{1}V_{2}\ldots V_{k} \quad k \geq 3$, quindi per compensare introduco nelle regole nuove $A \to W_{1}A_{1},\ A_{1} \to W_{2} A_{2},\ A_{2}\to W_{3}A_{3}\ \ldots\ A_{k-2} \to W_{k-2}W_{k}$
   **Esempio:** $A \to aBC$
   $A \to a A_{1}$
   $A_{1} \to BC$
   dopodiché $A \to aA_{1}$ (che non è ancora in CFG) diventa $A \to U A_{1}$ e $U \to a$, dove $U$ è una variabile d'appoggio introdotta adesso.

# Esercizio

#ŧodo

Regole originali

- $S \to A S A \mid aB$
- $A \to B \mid S$
- $B \to b \mid \varepsilon$

**Primo passaggio**: aggiunta di $S_{0}$.

- $S_{0} \to S$
- $A \to ASA \mid aB$
- $A \to B \mid S$
- $B \to b \mid \varepsilon$

**Secondo passaggio**: togliamo ogni $\varepsilon$ regola la cui variabile a sinistra appare nella destra di un'altra regola.

- $S_{0} \to S$
- $S \to ASA \mid aB \mid a$
- $A \to B \mid S \mid \varepsilon$
- $B \to b$

Abbiamo dovuto introdurre $A \to \varepsilon$ per togliere $B \to \varepsilon$, ma va anche questa va tolta. L'unica regola che deriva $A$ è $S \to ASA$, quindi per preservare $A \to \varepsilon$ senza scriverla esplicitamente dobbiamo dare la responsabilità di derivare $\varepsilon$ non più ad $A$ ma a $S$, quindi introdurre $S \to SA \mid AS \mid S$ e rimuovere $A \to \varepsilon$.

- $S_{0} \to S$
- $S \to ASA \mid aB \mid a \mid SA \mid AS \mid S$
- $A \to B \mid S$
- $B \to b$

**Terzo passaggio**: togliamo le regole unitarie.

- Togliamo $S_{0} \to S$ e per compensare aggiungiamo $S_{0} \to ASA \mid aB \mid a \mid SA \mid AS$.
- Togliamo $A \to B$ e per compensare aggiungiamo $A \to b$.
- Togliamo $A \to S$ e per compensare aggiungiamo $A \to ASA \mid aB \mid a \mid SA \mid AS \mid S$.

Otteniamo:

- $S_{0} \to ASA \mid aB \mid a \mid SA \mid AS$
- $S \to ASA \mid aB \mid a \mid SA \mid AS$
- $A \to b \mid ASA \mid aB \mid a \mid SA \mid AS$
- $B \to b$

**Quarto passaggio**: convertiamo tutte le rimanenti regole con almeno una variabile a destra in regole che hanno esclusivamente due variabili a destra, aggiungendo variabili d'appoggio.