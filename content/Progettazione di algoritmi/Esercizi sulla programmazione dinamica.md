---
updated_at: 2026-04-23T17:29:28.409+02:00
---
# Contare le sottostringhe di una stringa composta da un alfabeto ternario $\{0, 1, 2\}$ che non contengono $12$ e $22$ in $O(n)$.

Usiamo una tabella unidimensionale ([[array]]) $T$ lunga $n$. Mettiamo in $T[i]$ le stringhe buone lunghe $i$.

Le stringhe buone lunghe $i$ possono rientrare in tre casi possibili:

- quelle che finiscono con $0$:
	- la sottostringa fino al penultimo carattere può terminare in $0, 1, 2$, quindi va bene una qualsiasi delle stringhe contate da $T[i-1]$.
- quelle che finiscono con $1$:
	- la sottostringa fino al penultimo carattere può terminare in $0, 1, 2$, quindi va bene una qualsiasi delle stringhe contate da $T[i-1]$.
- quelle che finiscono con $2$:
	- la sottostringa fino al penultimo carattere può terminare solo con $0$, quindi qualsiasi stringa della forma `stringa di quelle contate da T[i-2] + "0"`, quindi esistono $T[i-2]$ stringhe valide in questo caso.

Riassumendo, $T[i] = 2T[i-1] + T[i-2]$.

I casi base sono $T[0] = 1,\ T[1] = 3$.

``` python
def conta(n):
     T = [0] * (n+1)
     T[0], T[1] = 1, 3
     for i in range(2, n+1):
         T[i] = 2*T[i-1] + T[i-2]
     return T[-1]

```

# Contare le sottostringhe di una stringa composta da un alfabeto ternario $\{0, 1, 2\}$ che non contengono $000$, $010$, $020$.

Le stringhe buone lunghe $T[i]$ possono terminare con i caratteri:

```
[ultimo carattere]
0
	[penultimo carattere]
	0
		[terzultimo carattere]
		0 (invalide)
		1 (valide, T[i-3] stringhe)
		2 (valide, T[i-3] stringhe)
	1
		0 (invalide)
		1 (valide, T[i-3] stringhe)
		2 (valide, T[i-3] stringhe)
	2
		0 (invalide)
		1 (valide, T[i-3] stringhe)
		2 (valide, T[i-3] stringhe)
1 (valide, T[i-1] stringhe)
2 (valide, T[i-1] stringhe)
```
