---
updated_at: 2026-10-19T12:55:09.125+02:00
---
# [[algebra di Boole|Booleani]] di church

### Valori

$$
\text{true} \equiv \text{Fn}\ xy \implies x \\
\text{false} \equiv \text{Fn}\ xy \implies y
$$

Che è uno short hand per:

$$
\text{true} \equiv\ \text{Fn}\ x \implies \text{Fn}\ y \implies x \\
\text{false} \equiv\ \text{Fn}\ x \implies \text{Fn}\ y \implies y
$$

## Operazioni

$$
\text{not} \equiv \text{Fn}\ Z \implies \text{Fn}\ xy \implies Zyx
$$

nj_sml

Se la applichiamo a un booleano di Church, la funzione ci da un booleano vero?

#todo Si dimostra che la funzione ifthenelse $\text{Fn}\ z \implies z$ è un booleano di Church. L'ifthenelse è una proprietà dei booleani, i booleani *sono* degli ifthenelse.