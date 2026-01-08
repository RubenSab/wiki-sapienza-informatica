---
updated_at: 2026-01-08T13:46:32.585+01:00
---
> È un [[gruppo]] $G$ i cui elementi sono le [[permutazioni]] di un [[insieme|insieme]] $M$ e la cui operazioni è la *composizione* delle permutazioni in $G$.

> In particolare, il gruppo di tutte le permutazioni di un insieme $M$ si chiama ***gruppo simmetrico*** di $M$, scritto come $\text{Sym(M)}$ o $S_{n}$, dove $n$ è la [[cardinalità]] di $M$.


Esempio:

- $M = \{a, b, c\}$
- $S_{3} = \{(a\ b\ c), (a\ c\ b), (b\ a\ c), (b\ c\ a), (c\ a\ b), (c\ b\ a)\}$

# Terminologia

> Il *grado* di un gruppo di permutazioni di un insieme **finito** $M$ è il numero degli elementi di $M$.

# Operazione di composizione

Consideriamo $S_{4}$ e due suoi elementi $\sigma = \begin{pmatrix} 1\ 2\ 3\ 4 \\ 2\ 1\ 4\ 3 \end{pmatrix}$ e $\tau = \begin{pmatrix} 1\ 2\ 3\ 4 \\ 2\ 4\ 1\ 3\end{pmatrix}$.
La composizione $\sigma \tau$ è $\begin{pmatrix} 1\ 2\ 3\ 4 \\ 2\ 4\ 1\ 3 \\ 1\ 3\ 2\ 4 \end{pmatrix} = \begin{pmatrix} 1\ 2\ 3\ 4 \\ 1\ 3\ 2\ 4 \end{pmatrix} = (1)(2\ 3)(4) = (2\ 3)$

Però la composizione $\tau \sigma$ è $\begin{pmatrix} 1\ 2\ 3\ 4 \\ 4\ 2\ 3\ 1 \end{pmatrix} = (1\ 4)$

> $\sigma \tau \ne \tau \sigma$: abbiamo appena dimostrato che $S_{4}$ non è un [[gruppo abeliano]].

> La [[gruppo di permutazioni|composizione]] di cicli a supporti disgiunti è commutativa.

> Teorema: ogni permutazione si *decompone* in modo unico come prodotto di cicli disgiunti.

> Teorema: ogni permutazione è prodotto di trasposizioni ("basta" vedere la proprietà sui cicli, infatti se ogni ciclo è prodotto di trasposizioni, allora ogni prodotto di cicli è prodotto di trasposizioni, ma ogni trasposizione è prodotto di cicli).

# Isomorfismo con $\mathbb{Z} / n\mathbb{Z}$

> Esiste un **unico** [[isomorfismo]] $\phi$ che si può trovare tra un [[sottogruppi#^2d81e6|sottogruppo generato da un elemento]] $\mu$ di un gruppo di permutazioni $G$ (quindi generato **componendo** la permutazione $\mu$ con se stessa un numero variabile di volte) e un [[sottogruppi|sottogruppo]] $\mathbb{Z} / n\mathbb{Z} < \mathbb{Z}$ è definito come segue:

$$
\phi:\ H \to \mathbb{Z}/\text{ord}(\mu)\mathbb{Z}
$$

$$
\phi(\mu^{k}) = \overline{k} = k + \text{ord}(\mu)\mathbb{Z}
$$

## Esempio

Sia $\mu = \begin{pmatrix} 1 & 2 & 3 & 4 & 5 & 6 & 7 & 8 \\ 6 & 2 & 7 & 5 & 3 & 1 & 8 & 4 \end{pmatrix}$

$\mu$ può essere scomposta in cicli a supporto disgiunto: $\mu = (2)(1\ 6)(3\ 7\ 8\ 4\ 5) = (1\ 6)(3\ 7\ 8\ 4\ 5)$

$\text{ord}(\mu) = \text{mcm}(\text{ord}(1 \ 6), \text{ord}(3\ 7\ 8\ 4\ 5)) = \text{mcm}(2, 5) = 10$

$$
\phi:\ H \to \mathbb{Z}/10\mathbb{Z}
$$

$$
\phi(\mu^{k}) = \overline{k} = k + 10\mathbb{Z}
$$

Intuitivamente, l'ordine di $\mu$ è il numero composizioni di $\mu$ con se stessa necessario per **ritrovare** $\mu$.

$$
\mu^{10} = \mu \circ \mu \circ \mu \circ \mu \circ \mu \circ \mu \circ \mu \circ \mu \circ \mu \circ \mu \circ \mu\ = \mu \quad \implies \quad \text{ord}(\mu) = 10
$$

Dato che $\mu^{10} = \mu$, allora $\mu^{n} = \mu^{10 + k}$. È evidente che questa uguaglianza genera 10 [[classe di equivalenza|classi di equivalenza]], ognuna corrispondente a un $n \in [0, 9]$, dove la classe $[a] = [a \mod 10]$.

Ciò corrisponde esattamente a $\mathbb{Z} / 10\mathbb{Z}$.

# Esistono sono gruppi $S_{n}$ abeliani?

I gruppi $S_{1}$ e $S_{2}$ sono abeliani, invece quelli con $S_{n}, n \geq 3$ non sono abeliani.

Script che lo dimostra per $S_{n \in [1, 7]}$:

``` python
from itertools import permutations, product

def transpose(t: tuple, element: int):
    return t[element - 1]

def check_composition_commutes(a: tuple, b: tuple) -> bool:
    elements = set(a)
    for element in elements:
        ab = transpose(a, transpose(b, element))
        ba = transpose(b, transpose(a, element))
        print(f'{a}∘{b} applicata a {element} {[f"non commuta ({ab=}, {ba=})", f"commuta (ab=ba={ab})"][ab == ba]}')
        if ab != ba: return False
    return True

def check_sym_group_commutes(n: int) -> bool:
    perms = list(permutations(range(1, n+1)))
    for a, b in product(perms, perms):
        if not check_composition_commutes(a, b):
            return False
    return True

for n in range(1, 7):
    print(f'S_{n}: {["non è", "è"][check_sym_group_commutes(n)]} abeliano\n')
```

``` python
def check_sym_group_commutes(n: int) -> bool:
    perms = list(permutations(range(1, n+1)))
    rez = [check_composition_commutes(a, b) for a, b in product(perms, perms)]
    return f"S_{n}: {rez.count(True)}/{len(rez)} = {rez.count(True)/len(rez)*100}%"

for n in range(1, 7):
    print(check_sym_group_commutes(n))
```

| $n$ | Composizioni commutative di $S_{n}$ (Coincide con https://oeis.org/A053529) | Composizioni totali di $S_{n}$ |
| --- | --------------------------------------------------------------------------- | ------------------------------ |
| 1   | 1 (100%)                                                                    | 1                              |
| 2   | 4 (100%)                                                                    | 4                              |
| 3   | 18 (50%)                                                                    | 36                             |
| 4   | 120 (20.833%)                                                               | 576                            |
| 5   | 840 (5.833%)                                                                | 14400                          |
| 6   | 7920 (1.527%)                                                               | 518400                         |
| 7   | 75600 (0.298%)                                                              | 25401600                       |
| 8   | - (16 GB di RAM sono troppo pochi)                                          | -                              |

