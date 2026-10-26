---
updated_at: 2026-10-26T15:13:29.600+01:00
---
$$
\text{Exp} = \begin{cases}
k ::= \emptyset \mid 1 \mid \ldots \mid \text{True} \mid \text{False} \\
M, N ::= \underset{\text{costante}}{\underbrace{\mathcal{k}}} \mid \underset{\text{variabile}}{\underbrace{x}} \mid N+M \mid M < N
\end{cases}
\\
\underset{\text{programmi}}{\underbrace{p, q}} ::= \text{skip} \mid p; q \mid \underset{\text{assegnamento}}{\underbrace{x := M}} \mid \underset{\text{inizializzazione}}{\underbrace{\text{var}\ x = M\ \text{in}\ p}} \mid \text{while}\ M\ \text{do}\ p \mid \text{if}\ M\ \text{then}\ p\ \text{else}\ q
$$

> Nota: IMP contiene il [[linguaggio di programmazione]] [[Linguaggio EXP|EXP]].

- **skip** è il programma che non fa niente (lascia lo *store* invariato).
- Il `:=` è l'**assegnamento**.
- `;` è un costruttore dell'[[algebra induttiva]] dei programmi di IMP che dati due programmi crea un programma che è la loro concatenazione.

# [[semantica|Semantica]] operazionale 

> Rispetto a EXP e a [[Linguaggio FUN|FUN]], l'ambiente non contiene i valori o le espressioni associate al nome di una variabile, perché la mappatura si fa in due step: l'**ambiente** mappa i nomi delle variabili alle locazioni di [[memoria]] e lo **store** mappa le locazioni ai valori.

- $\text{Loc} = \{l_{1}, l_{2}, l_{3}, \ldots\}$ (è un [[insieme]] di locazioni di memoria)
- L'[[ambiente]] è $E \in \text{Env} = \text{Var} \to \text{Loc}$ ($\text{Var}$ è un dominio finito)
- Lo store mappa locazioni a valori: $S \in \text{Store} = \text{Loc} \to \text{Val}$ ($\text{Loc}$ è un dominio finito)

> $\overset{M}{\rightsquigarrow}$ è una [[relazione]] in $\text{Env} \times \text{Exp} \times \text{Store} \times \text{Val}$. Non può essere una
> [[funzione]] $\text{Env} \times \text{Exp} \times \text{Store} \to \text{Val}$ perchè non sarebbe deterministica, cioè potrebbe avere più di un risultato, nessun risultato (va in loop o eccezione) o valori validi in diversi istanti temporali. Ad esempio la variabile potrebbe essere l'orologio di sistema.
> Volendo si potrebbe anche formalizzare $\overset{M}{\rightsquigarrow}$ come $\text{Env} \times \text{Exp} \times \text{Store} \to \mathcal{P}(\text{Val})$, cioè l'[[insieme delle parti]] dei valori.

Formalmente:

$$
\overset{M}{\rightsquigarrow} \subseteq \text{Env} \times \text{Exp} \times \text{Store} \times \text{Val}
$$

Il fatto che per gli elementi della tupla $(E, M, S, v)$ valga la relazione, cioè $(E, M, S, v) \subseteq \overset{M}{\rightsquigarrow}$, si può scrivere come la [[regola di inferenza]] $E \vdash M, S \overset{M}{\rightsquigarrow} v$: "L'espressione $M$, nel contesto dello store $S$, valutata nell'ambiente $E$, vale $v$".

Similmente, $\overset{p}{\rightsquigarrow} \subseteq \text{Env} \times \text{Imp} \times \text{Store} \times \text{Store}$ equivale a $E \vdash p,\ S \overset{S}{\rightsquigarrow} S'$: "Il programma $p$, nel contesto dello store $S$, valutato nell'ambiente $E$, vale $S'$".

> Ciò vuol dire che il risultato dei programmi non è definito dal ritorno di un valore, ma dai valori finali dello store (come cambia lo store dopo l'esecuzione).

*Forma dei sequenti* del linguaggio IMP:

- Valutazione delle espressioni: $E \vdash M,\ S \overset{M}{\rightsquigarrow} v$.
- Valutazione dei programmi: $E \vdash p,\ S \overset{S}{\rightsquigarrow} S'$.
- Assegnazione di valori a locazioni dello store: $E \vdash x,\ S \overset{M}{\rightsquigarrow} v \quad (\text{se}\ E(x) = l \land S(l) = v)$.
- Addizione di espressioni: $\frac{E \vdash M,\ S \rightsquigarrow v_{1},\quad E \vdash N, S \rightsquigarrow v_{2}}{E \vdash M + N ,\ S \rightsquigarrow v}\ (\text{se}\ v = v_{1} + v_{2})$.
- Confronto tra espressioni: $\frac{E \vdash M,\ S \rightsquigarrow v_{1},\quad E \vdash N, S \rightsquigarrow v_{2}}{E \vdash M < N ,\ S \rightsquigarrow \text{true}}\ (\text{se}\ v_{1} < v_{2})$.
- Esecuzione del programma skip: $E \vdash \text{skip}, S \rightsquigarrow S$.
- Concatenazione di programmi: $\frac{E \vdash p,\ S \rightsquigarrow S',\quad E \vdash q, S' \rightsquigarrow S''}{E \vdash p;q,\ S \rightsquigarrow S''}$.
- If then else: $\frac{E \vdash M,\ S \rightsquigarrow \text{true (oppure false)},\quad E \vdash p\ (\text{oppure}\ q), S \rightsquigarrow S'}{E \vdash \text{if}\ M\ \text{then}\ p\ \text{else}\ q,\ S \rightsquigarrow S'}$.
- While:
	- condizione falsa: $\frac{E \vdash M, S \rightsquigarrow \text{false}}{E \vdash \text{while}\ M\ \text{do}\ p\ S \rightsquigarrow S}$ (non va in esecuzione, $S$ è immutato, equivalente a skip).
	- condizione vera: $\frac{E \vdash M, S \rightsquigarrow \text{true},\quad E \vdash p, S \rightsquigarrow S', \quad E \vdash \text{while}\ M\ \text{do}\ p, S' \rightsquigarrow S''}{E \vdash \text{while}\ M\ \text{do}\ p\ S \rightsquigarrow S''}$. L'inferenza è ricorsiva perché per valutare il while (nella conclusione sotto) serve valutare il while (nella premessa sopra). Si esce solo quando $M$ valuta a false.
