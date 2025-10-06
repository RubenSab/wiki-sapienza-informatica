---
updated_at: 2025-10-06T14:35:24.130+02:00
---
> Per scegliere $k$ elementi da $n$ senza ripetizioni, senza ordine, bisogna [[disposizioni senza ripetizioni|scegliere k elementi da n senza ripetizioni e con ordine]], poi bisogna dimenticare l'ordine (rimuovendo i duplicati).

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

Esempio 1:

Se $n$ invitati si stringono la mano a una festa e nessuno si stringe la mano con se stesso, quante strette di mano ci sono? Cioè quante coppie non ordinate si possono formare con $n$ persone?

$$
\frac{n!}{2!(n-1)!}=\binom{n}{2}=\frac{n\cdot (n-1)}{2}
$$

Esempio 2:

Il una società di 124 persone va eletto un gruppo di 3 persone di rappresentanza.

$$
\frac{124!}{3!(121)!} = \frac{124\cdot 123 \cdot 122}{3 \cdot 2} = 124 \cdot 41 \cdot 61
$$

Ci sono 310124 modi diversi di farlo.