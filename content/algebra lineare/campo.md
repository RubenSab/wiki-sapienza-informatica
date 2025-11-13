---
updated_at: 2025-11-12T20:24:44.468+01:00
---
> Un campo è un [[anello|anello commutativo]] tale che $A^{\times} = A - \{0\}$, cioè tutti gli elementi diversi dal neutro additivo sono invertibili.

$\mathbb{Q}, \mathbb{R}, \mathbb{C}$ (infiniti) sono campi, ma anche tutti gli [[insieme quoziente|insiemi quozienti]] $\mathbb{F}_{p}=\frac{\mathbb{Z}}{p\mathbb{Z}}$ (finiti!) su cui sono definite addizione e moltiplicazione; invece $\mathbb{Z}$ non è un campo, perché $\mathbb{Z}^{\times} = \{-1, 1\}$ è diverso da $\mathbb{Z} - \{0\}$.

I campi finiti possono essere classificati:

> Per ogni potenza di un primo $q = p^{\alpha} \quad \alpha \geq 1$ esiste un unico campo finito $\mathbb{F}_{q}$ con $q$ elementi.

Se $\alpha = 1$ sappiamo come costruirli, se $\alpha \geq 2$ è più difficile. Si potrebbe pensare ad esempio che l'[[anello#^3f551f|insieme degli invertibili]] $(\frac{\mathbb{Z}}{4\mathbb{Z}})^{\times} = \{\overline{1}, \overline{3}\}$ sia un campo, ma ciò è falso perché 4 non è primo.

# Esempio di campo: $\mathbb{F}^{\times}_{5}$ (si vedrà che è anche un gruppo)

> $\mathbb{F}^{\times}_{5} = \{\overline{1}, \overline{2}, \overline{3}, \overline{4}\}$ ([[classe di equivalenza|classi]] modulo 5 ($\mathbb{F}_{5}$) senza $\overline{0}$, perché non è invertibile).

Tabella del prodotto $\cdot$ (operazione ereditata da $\mathbb{Z}$): notare la simmetria della tabella, causata dalla simmetria di questa operazione.

| $\cdot$ | 1           | 2           | 3           | 4           |
| ------- | ----------- | ----------- | ----------- | ----------- |
| **1**   | $\boxed{1}$ | 2           | 3           | 4           |
| **2**   | 2           | 4           | $\boxed{1}$ | 3           |
| **3**   | 3           | $\boxed{1}$ | 4           | 2           |
| **4**   | 4           | 3           | 2           | $\boxed{1}$ |

> Si vede dalla tabella $\left(\boxed{1}\right)$ che a differenza del prodotto in $\mathbb{Z}$, il prodotto su $\mathbb{F}^{\times}_{5}$ è chiuso, non per un assioma, ma per la definizione stessa di prodotto: $G \times G \to G$.

> N.B.: $(\mathbb{F}^{\times}_{5}, \cdot, \overline{1})$ è un [[gruppo abeliano]]: $*$ è il prodotto $\cdot$ di classi e $e = \overline{1}$.



