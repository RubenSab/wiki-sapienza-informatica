---
updated_at: 2026-01-25T08:45:28.949+01:00
---
> Per scegliere $k$ elementi da $n$ senza ripetizioni, senza ordine, bisogna [[disposizioni senza ripetizioni|scegliere k elementi da n senza ripetizioni e con ordine]], poi bisogna dimenticare l'ordine sia dei $k-n$ elementi che non ci interessano, dividendo per $(n-k)!$ come nelle [[disposizioni senza ripetizioni]], sia l'ordine dei $k$ elementi che non ci interessano, dividendo per $k!$.

Ad esempio:

```
3 5 4 X X
3 4 5 X X
4 5 3 X X
4 3 5 X X
5 4 3 X X
5 3 4 X X
```

Vanno considerati come un'unica scelta ${3, 4, 5}$

Quindi la formula è

$$\frac{n!}{k!(n-k)!}$$

- $n!$ ordina tutti gli elementi
- $(n-k)!$ dimentica l'ordine di quelli scartati
- $k!$ dimentica l'ordine **anche di quelli scelti**

> Questa formula è la definizione del [[coefficiente binomiale]].

# Esempi
## 1

Se $n$ invitati si stringono la mano a una festa e nessuno si stringe la mano con se stesso, quante strette di mano ci sono? Cioè quante coppie non ordinate si possono formare con $n$ persone?

$$
\frac{n!}{2!(n-1)!}=\binom{n}{2}=\frac{n\cdot (n-1)}{2}
$$

## 2

Il una società di 124 persone va eletto un gruppo di 3 persone di rappresentanza:

$$
\frac{124!}{3!(121)!} = \frac{124\cdot 123 \cdot 122}{3 \cdot 2} = 124 \cdot 41 \cdot 61
$$

ci sono 310124 modi diversi di farlo.

## 3: Coefficiente multinomiale

^408300

Scopriamo come dividere $n=10$ elementi in 3 gruppi, $G_{1}$ di 3 elementi, $G_{2}$ di 5 elementi e $G_{3}$ di 2 elementi.

Possiamo fare così:

1. Scegliamo i 3 elementi da mettere in $G_{1}$, avremo $\binom{10}{3}$ modi;
2. Tra i $n-3 = 7$ rimanenti, scegliamo 3 elementi da mettere in $G_{2}$ avremo $\binom{7}{5}$ modi;
3. Le restanti ($2$) vanno in $G_{3}$ avremo $\binom{2}{2}$ modi.

In totale abbiamo $\binom{10}{3} \cdot \binom{7}{5} \cdot \binom{2}{2} = \frac{10!}{3!\cdot 5!\cdot 2!}$ modi, che si possono scrivere anche come $\binom{10}{3\ 5\ 2}$, che è un ***coefficiente multinomiale***.

---

In generale, i modi per dividere $n$ elementi in $3$ gruppi di $k_{1},\ k_{2},\ k_{3}$ elementi ciascuno con $k_{1} + k_{2} + k_{3} = n$ è

$$
\binom{n}{k_{1}} \cdot \binom{n-k_{1}}{k_{2}} \cdot \binom{n-(k_{1}+k_{2})}{k_{3}} = \binom{n}{k_{1}\ k_{2}\ k_{3}}
$$