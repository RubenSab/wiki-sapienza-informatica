---
updated_at: 2026-10-16T09:30:09.837+02:00
---
> Una [[grammatica acontestuale (CFG)]] è in **forma normale** se oni sua regola è nella forma $A \to BC$ oppure $A \to a$. Dove $A, B, C \in V,\quad a \in \Sigma,\quad B,C \notin S$. È ammessa anche la regola $S \to \varepsilon$.

> Teorema: ogni CFG ammette una CFG equivalente in forma normale.

1. Dobbiamo trasformare le regola della CFG. Per prima cosa aggiungo $S_{0}$, la nuova variabile iniziale e le regole $S_{0} \to S$.
2. Passiamo poi alle $\varepsilon$-regole: $A \to \varepsilon$. Per ogni occorrenza di $A$ sul lato destro di una regola, aggiungo nuove regole con occorrenza cancellata. (praticamente per poter togliere $A \to \varepsilon$ si applica $A \to \varepsilon$ a tutte le regole vecchie).
   **Esempio**:
   $A \to \varepsilon$
   $B \to u A v$, con $u, v$ stringhe di variabili/terminali.
   $\implies B \to uv$
   **Altro esempio**:
   $B \to u A v A w$
   $\implies B \to u v w \mid u A v w \mid u v A w \mid u A v A w$
   **Altro esempio**:
   $B \to C \quad C \to A \mid c$ diventano $B \to A \mid c$ e $C \to A \mid c$
3. Togliamo le regole unitarie: $A \to B$. Per ogni occorrenza di regole $B \to u$, aggiungo $A \to u$. ($u$ sempre sequenza di variabili/terminali)
   ![[subway-surfers.gif]]
   *(piccola gif a scopo di intrattenimento)*
4. Infine tolgo tutte le $A \to u_{1},\ u_{2},\ \ldots,\ u_{k} \quad k \geq 3$, quindi per compensare introduco nelle regole nuove $A \to w_{1}A_{1},\ A_{1} \to w_{2} A_{2},\ A_{2}\to w_{3}A_{3}\ \ldots\ A_{k-2} \to w_{k-2}w_{k}$
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

Primo passaggio: aggiunta di $S_{0}$.

- $S_{0} \to S$
- $A \to ASA \mid aB$
- $A \to B \mid S$
- $B \to b \mid \varepsilon$

Secondo passaggio: togliamo le $\varepsilon$ regole.

- $S_{0} \to S$
- $S \to ASA \mid aB \mid a$
- $a \to B \mid S \mid \varepsilon$
- $B \to b$

Terzo passaggio: togliamo le regole unitarie.

- togliamo $S_{0} \to S$ e per compensare aggiungiamo $S_{0} \to ASA \mid aB \mid a \mid SA \mid AS \mid S$