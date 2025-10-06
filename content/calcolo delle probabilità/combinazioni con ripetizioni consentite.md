---
updated_at: 2025-10-06T15:00:32.108+02:00
---
*Vedi [[contare con le biezioni]]*

> In quanti modi posso scegliere $k$ elementi da $n$, senza ordine e con possibili ripetizioni?

Definiamo un insieme $A$ in cui ogni elementi è modo di scegliere $k$ elementi da $n$ senza ordine e con possibili ripetizioni.

Qual'è l'insieme con cui possiamo mettere $A$ in biezione?

Esempio: Scelgo 5 elementi da $\Omega = \{a, b, c, d\}$ con possibili ripetizioni.

Usiamo l'[[algoritmo]] *sticks and stars*.

$$
\{a, b, a, d, a\} \mapsto *** \mid * \mid\ \mid * \mid\ \mapsto\ \{a, a, a, b, d\}
$$

L'insieme di partenza e di arrivo è lo stesso, non considerando l'ordinamento, perché la [[funzione]] è una biezione. Questa funzione è effettivamente una [[funzioni di codifica e decodifica|funzione di codifica]] invertibile.

Ogni elemento di $B$ è il numero $k$ di *stars* + il numero $n-1$ di *sticks*.

Determiniamo $|B|$. La stringa di lunghezza $k+n-1$ (cioè la composizione di ogni elemento di $B$) è univocamente determinata dalla posizione delle *stars*, che sono $k$. Quindi devo specificare $k$ posizioni da $k+n-1$ ([[combinazioni senza ripetizioni]]), quindi:

$$
\binom{k+1}{k} = \binom{k+n-1}{n-1}
$$

Quindi la formula generale è:

$$
\binom{k+n-1}{k} = \frac{(k+n-1)!}{k!\cdot(n-1)!}
$$


---

**Esempio 1**: Ho 100 amici, ne devo selezionare 72. Quante possibili scelte ho?

$$
\binom{100}{72}=\frac{100!}{72!28!}
$$

Che è lo stesso risultato che avrei ottenuto scegliendo chi escludere per la proprietà del [[coefficiente binomiale]]:

$$
\binom{100}{28}=\binom{100}{72}
$$

---

**Esempio 2**: Quante parole di lunghezza 7 ci sono con esattamente 3 A?

Scegliamo dove posizionare le 3 A (combinazione senza ripetizione): $\binom{7}{3}$

Scegliamo come mettere i caratteri rimanenti (disposizioni con ripetizioni): $25^{4}$

Totale = $\binom{7}{3} \cdot 25^{4} = 35 \cdot 25^{4}$

---

**Esempio 3:** Quante funzioni ci sono $f : \{1, 2, \ldots, n\} \mapsto \{1, 2, \ldots, k\}$ e quante strettamente crescenti?

Numero di funzioni ([[permutazioni]]): $k^{n}$

Per avere funzioni strettamente crescenti assumiamo $k \geq n$.

1. Una funzione strettamente crescente è codificata univocamente (quindi anche in maniera invertibile) dal suo codominio e il suo dominio (che in questo caso è sempre lo stesso per le varie funzioni).

2. Per ottenere tutti i codominii, quindi tutte le funzioni strettamente crescenti, bisogna scegliere $n$ elementi da $k$. Quindi $\binom{k}{n}$.