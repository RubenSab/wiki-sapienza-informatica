---
updated_at: 2025-12-04T11:20:09.701+01:00
---
> La teoria degli anelli si fonda sull'**astrazione** delle proprietà delle operazioni sull'[[insieme|insieme]] dei [[numeri interi relativi]] $\mathbb{Z}$, le quali vengono definite su un sull'insieme generico detto [[anello]].

# Operazioni in $\mathbb{Z}$

## Assiomi

$\mathbb{Z}$ è dotato di due operazioni **binarie** (addizione e moltiplicazione) più una **unaria**, (l'opposto). Esse sono definite attraverso questi assiomi:

- L'addizione $+$ è **commutativa** ($a+b=b+a$) e **associativa** ($a+(b+c)=(a+b)+c$).
- Anche la moltiplicazione $\cdot$ è **commutativa** ($ab=ba$) e **associativa** ($(ab)c=a(bc)$).
- La moltiplicazione è **distributiva** sull'addizione ($a(b+c) = ab+ac$).
- Esiste il *neutro additivo* $0$ con $a+0=0+a = a$.
- Esiste il *neutro moltiplicativo* $1$ con $a\cdot 1 = 1 \cdot a = a$.

### Definizione induttiva del prodotto $\cdot$

La moltiplicazione $a \cdot b$ in $\mathbb{Z}$ si può definire:

- per $b>0\to a \cdot b= \sum_{k = 0}^{b}{a_{k}}$, cioè ripetendo l'addizione di $a$ ad $a$ per $b$ volte.
- per $b<0 \to a \cdot b = -(a \cdot (-b))$, cioè usando la definizione di prodotto per $b > 0$ e l'opposto.
- per $b \cdot 0 = 0$ per definizione di neutro moltiplicativo.

### Definizione di sottrazione $-$

Usando l'addizione e l'opposto: $a-b = a+(-b)$.

## Tricotomia

Definiamo $\geq$ come segue: $a\geq b \iff a-b\in\mathbb{N}$.

> In $\mathbb{Z}$ vale la *tricotomia*, cioè $\forall a, b \in \mathbb{Z},\quad (a \geq b) \implies (a<b) \land (a=b) \land (a>b)$

> N.B.: $\exists n \in \mathbb{N}\ \forall x \in \mathbb{N}\ (n \leq x)$ ma $\nexists z \in \mathbb{Z}\ \forall x \in \mathbb{Z}\ (z \leq x)$, cioè $\mathbb{N}$ soddisfa il principio del minimo (o buon ordinamento), ma $\mathbb{Z}$ no. Ciò si dimostra con $\forall z \in \mathbb{Z}\ (z-1 \in \mathbb{Z} \land z-1<z) \implies \nexists z \in \mathbb{Z}\ \forall x \in \mathbb{Z}\ (z \leq x)$.

### Compatibilità degli elementi di $\mathbb{Z}$ con $+, -, \cdot$

Per $a, b, c, d \in \mathbb{Z}$ vale che:

- $a<b \implies -b<-a$
- $a \leq b \land c \leq d \implies a + c \leq b + d$
- $0 < c \leq d \land a<b \implies ac<bd$

## Legge di cancellazione in $\mathbb{Z}$

Dagli assiomi si deduce che $a, b, c \in \mathbb{Z} \land a \neq 0 \land ab = ac \implies b = c$

### Dimostrazione

1. per assurdo supponiamo $b \neq c$,
2. per la proprietà distributiva di $\cdot$ $ab-ac=a(b-c)$,
3. per tricotomia assumiamo $b>c$, cioè $b-c>0$, cioè $b - c \neq 0$,
4. per definizione $a \neq 0$,
5. per l'unicità del neutro moltiplicativo $b - c \neq 0 \land a \neq 0 \implies a(b-c)\neq 0 \implies ab \neq ac$,
6. per contraddizione dell'assurdo $b = c$.