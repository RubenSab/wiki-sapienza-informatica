---
updated_at: 2025-03-07T00:02:05.884+01:00
---
> Una serie numerica $a_{n}$ è la [[successione]] delle somme (somme parziali) dei primi $n$ termini di una successione $a_{n}$.

> N.B.: Sommare infiniti termini non è un procedimento naturale, quindi bisogna introdurre coerentemente un modo di farlo. Bisogna dare un significato matematicamente valido a: $$S_{n}=\sum_{n=1}^{+\infty}a_{n}$$

# convergenza e divergenza

- se $\exists \lim_{n\to +\infty}{s_{n}}$ allora $\sum_{n=1}^{+\infty}a_{n} \in \mathbb{R}$ ha un significato:
	- se la somma è uguale a un numero, la serie [[limiti di successioni|converge]].
	- se la somma è uguale a $\pm \infty$ allora la serie [[limiti di successioni|diverge]].
- se $\nexists \lim_{n\to +\infty}{s_{n}}$ allora $\sum_{n=1}^{+\infty}a_{n}$ è indeterminata, privo di significato.

## esempi

$a_{n}=(-1)^{n}$ oscilla tra $1$ e $-1$ quindi non converge, controlliamo se $S_{n}=\sum_{n=1}^{+\infty}a_{n}$
$S_{n}$ oscilla tra $0$ e $1$, quindi non converge.

## metodi per determinare la convergenza

- [[successione di cauchy]]
- [[teoremi dei limiti sulle successioni|teorema dei carabinieri]]
- [[confronto asintotico]]
# estensione della definizione

> N.B.: La definizione di serie fornita sopra è incompleta, infatti l'indice di partenza della sommatoria può essere un numero qualsiasi\*.

Infatti, *\*(solo se non si verificano forme indeterminate)* vale che $$\lim_{n\to +\infty}S_{n}=S \iff \lim_{n\to +\infty}(S_{n}-S)=0$$
Sostituendo $S$ e $S_{n}$ con le loro definizioni, otteniamo $$\lim_{n\to +\infty}\left( \sum_{k=1}^{n}a_{k} - \sum_{n=1}^{+\infty}a_{k} \right) = \lim_{n\to +\infty} \sum_{k=n+1}^{+\infty}a_{n}\ \ \ \to\ \ \ S_{n}-S = \sum_{k=n+1}^{+\infty}a_{n}$$
Quindi $n$ può essere un numero arbitrario.

# serie più comuni

- [[serie geometriche]]
- [[serie armoniche]]
- [[serie di Mengoli]]