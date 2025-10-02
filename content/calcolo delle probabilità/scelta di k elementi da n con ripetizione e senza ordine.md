---
updated_at: 2025-10-01T15:30:40.393+02:00
---
Scopriamo come dividere $n=10$ elementi in 3 gruppi, $G_{1}$ di 3 elementi, $G_{2}$ di 5 elementi e $G_{3}$ di 2 elementi.

Possiamo fare così:

1. Scegliamo i 3 elementi da mettere in $G_{1}$, avremo $\binom{10}{3}$ modi;
2. Tra i $n-3 = 7$ rimanenti, scegliamo 3 elementi da mettere in $G_{2}$ avremo $\binom{7}{5}$ modi;
3. Le restanti ($2$) vanno in $G_{3}$ avremo $\binom{2}{2}$ modi.

In totale abbiamo $\binom{10}{3} \cdot \binom{7}{5} \cdot \binom{2}{2} = \frac{10!}{3!\cdot 5!\cdot 2!}$ modi, che si possono scrivere anche come $\binom{10}{3\ 5\ 2}$, che è un *coefficiente multinomiale*.

---

In generale, i modi per dividere $n$ elementi in $3$ gruppi di $k_{1},\ k_{2},\ k_{3}$ elementi ciascuno con $k_{1} + k_{2} + k_{3} = n$ è

$$
\binom{n}{k_{1}} \cdot \binom{n-k_{1}}{k_{2}} \cdot \binom{n-(k_{1}+k_{2})}{k_{3}} = \binom{n}{k_{1}\ k_{2}\ k_{3}}
$$
