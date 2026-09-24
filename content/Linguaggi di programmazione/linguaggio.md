---
updated_at: 2026-09-24T20:48:48.939+02:00
---
> Lo studio di un linguaggio è lo studio della sua:

- [[sintassi]]
- semantica
- [[pragmatica]] (il "contesto" che contribuisce all'associazione di significato)

# Esempio di linguaggio formale

Definizione di elemento del linguaggio:

$$
E ::= 3 \mid 9 \mid \dots \mid E + E' \mid E * E'
$$

Definizione della [[funzione]] $\text{eval}$ che mappa l'[[insieme]] delle espressioni al loro significato.

$$
\text{eval}(E) =
\begin{cases}
\text{eval}(3) = 3 \\
\text{eval}(E_{1} + E_{2}) = \text{eval}(E_{1}) + \text{eval}(E_{2}) \\
\text{eval}(E_{1} * E_{2}) = \text{eval}(E_{1}) \times \text{eval}(E_{2}) \\
\end{cases}
$$

Non è una definizione [[induzione strutturale|induttiva]] ben definita di $\text{eval}$, perché sarebbe ambiguo come comportarsi in casi come $\text{eval}(2 * 3 + 1)$.

Però, adottando l'approccio della [[sintassi astratta]] ci si può liberare da questa ambiguità.