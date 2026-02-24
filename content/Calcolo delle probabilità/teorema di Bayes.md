---
updated_at: 2026-01-26T13:23:46.139+01:00
---
A volte è utile invertire il [[probabilità condizionata|condizionamento]], se ad esempio $\mathbb{P}(A \mid B)$ è difficile da calcolare ma $\mathbb{P}(B \mid A)$ è facile.

> Il teorema dice che per due [[evento|eventi]] $A$ e $B$ si ha che $\mathbb{P}(A \mid B) = \frac{\mathbb{P}(B \mid A) \cdot \mathbb{P}(A)}{\mathbb{P}(B)}$. Poi calcolando $\mathbb{P}(B)$ con la [[legge della probabilità totale]] otteniamo che

$$
\mathbb{P}(A \mid B) = \frac{\mathbb{P}(B \mid A) \cdot \mathbb{P}(A)}{\mathbb{P}(B \mid A)\cdot \mathbb{P}(A) + \mathbb{P}(B \mid A^{C}) \cdot \mathbb{P}(A^{C})}
$$

Dimostrazione:

$$
\mathbb{P}(A \mid B) = \frac{\mathbb{P} (A \cap B)}{\mathbb{P}(B)} = \frac{\mathbb{P}(B \mid A) \cdot \mathbb{P}(A)}{\mathbb{P}(B)} = \frac{\mathbb{P}(B \mid A) \cdot \mathbb{P}(A)}{\mathbb{P}(B \mid A)\cdot \mathbb{P}(A) + \mathbb{P}(B \mid A^{C}) \cdot \mathbb{P}(A^{C})}
$$

# Esempio 1

Contesto:

Alice guarda il meteo. Se è prevista pioggia, prende l'ombrello con probabilità 0.8, altrimenti lo prende con probabilità 0.25. La previsione è pioggia con probabilità 0.3.

> Calcolare la probabilità che Alice oggi prenda l'ombrello.

Sia $A = \{\text{Alice prende l'ombrello}\}$

```
- (B) prevista pioggia (0.3)
	- (A | B) Alice prende l'ombrello (0.8)
	- Alice non prende l'ombrello (0.2)
- (B^C) previsto sole (0.7)
	- (A | B^C) Alice prende l'ombrello (0.25)
	- Alice non prende l'ombrello (0.75)
```

Osservazioni:

- "Alice prende l'ombrello" nel caso $B$ è $\mathbb{P}(A \mid B)$ perché sono eventi condizionati
- "Alice prende l'ombrello" nel caso $B^{C}$ è $\mathbb{P}(A \mid B^{C})$ perché sono eventi condizionati

$$
\mathbb{P}(A) = \underset{0.8}{\mathbb{P}(A \mid B)} \cdot \underset{0.3}{\mathbb{P}(B)} + \underset{0.25}{\mathbb{P}(A \mid B^{C})} \cdot \underset{0.7}{\mathbb{P}(B^{C})} = 0.415
$$
Se invece avessimo chiesto:

> Incontrando Alice, e vediamo che ha l'ombrello. Qual è la probabilità che oggi il meteo preveda sole?

Basta riusare i dati precedenti e applicare il teorema di Bayes.

$$
\mathbb{P}(B^{C} \mid A) \underset{\text{Bayes}}{=} \frac{\mathbb{P}(B^{C} \cap A)}{\mathbb{P}(A)} = \frac{\mathbb{P}(A \mid B^{C}) \cdot \mathbb{P}(B^{C})}{\mathbb{P}(A)} = \frac{0.25 \cdot 0.7}{\underset{0.8}{\mathbb{P}(A \mid B)} \cdot \underset{0.3}{\mathbb{P}(B)} + \underset{0.25}{\mathbb{P}(A \mid B^{C})} \cdot \underset{0.7}{\mathbb{P}(B^{C})}} \approx 0.422
$$

---
# Esempio 2: falsi positivi

Contesto:

Un test per una mutazione genetica è accurato al $99\%$. Si sa che lo $0.5\%$ della popolazione ha la mutazione genetica.

```
- (B) mutazione (5/1000)
	- (A | B) positivo (99/100)
	- negativo (1/100)
- (B^C) assenza di mutazione (995/1000)
	- (A | B^C) positivo (1/100)
	- negativo (99/100)
```

> Fate il test, e esce positivo. Calcolare la probabilità che avete la mutazione genetica. $\mathbb{P}(B \mid A)$.

$$
\mathbb{P}(B \mid A) = \frac{\mathbb{P}(A \cap B)}{\mathbb{P}(A)}=\frac{\mathbb{P}(A \mid B)\cdot \mathbb{P}(B)}{\mathbb{P}(A)} = \frac{\mathbb{P}(A \mid B) \cdot \mathbb{P}(B)}{\mathbb{P}(A \mid B)\cdot \mathbb{P}(B) + \mathbb{P}(A \mid B^{C}) \cdot \mathbb{P}(B^{C})} = \frac{\frac{99}{100} \cdot \frac{5}{100}}{\frac{99}{100} \cdot \frac{5}{1000} + \frac{1}{100} \cdot \frac{995}{1000}} = 0.33
$$

---
# Esempio 3: partizionamento di $\Omega$ in 3 casi

Una scatola contiene 3 tipi diversi di lampadine, $A$, $B$ e $C$, in proporzione rispettivamente 20%, 30% e 50%.

Sappiamo che lampadine di tipo $A$, $B$ e $C$ durano almeno 1000 ore con probabilità $p_{A} = 0.7$, $p_{B} = 0.4$ e $p_{C} = 0.3$ rispettivamente. Si scelga una lampadina a caso.

## 1. calcolare la probabilità che la lampadina duri almeno 1000 ore.

Sia $E = \{\text{la probabilità che la lampadina duri almeno 1000 ore.}\}$. Vogliamo calcolare $\mathbb{P}(E)$

```
- scelgo la lampadina
	- (A) tipo A (20/100)
		- (p_A) dura almeno 1000 ore (primo "pezzo" di E) (0.7)
		- (1 - p_A) dura meno di 1000 ore
	
	- (B) tipo B (30/100)
		- (p_B) dura almeno 1000 ore (secondo "pezzo" di E) (0.4)
		- (1 - p_B) dura meno di 1000 ore
	
	- (C) tipo C (50/100)
		- (p_C) dura almeno 1000 ore (terzo "pezzo" di E) (0.3)
		- (1 - p_C) dura meno di 1000 ore
```

Usando il partizionamento di $\Omega$ e la legge delle probabilità totali:

$$
\mathbb{P}(E) = \mathbb{P}(E \cap A) + \mathbb{P}(E \cap B) + \mathbb{P}(E \cap C) = \underset{p_{A}}{\mathbb{P}(E \mid A)} \cdot \underset{\frac{20}{100}}{A} + \underset{p_{B}}{\mathbb{P}(E \mid B)} \cdot \underset{\frac{30}{100}}{B} + \underset{p_{C}}{\mathbb{P}(E \mid C)} \cdot \underset{\frac{50}{100}}{C}
$$

## 2. Si estrae una lampadina e si osserva che dura almeno 1000 ore. Calcolare la probabilità che la lampadina estratta è di tipo $A$.

Usando il risultato di $\mathbb{P}(E)$ calcolato nel punto precedente.
$$
\mathbb{P}(A \mid E) \underset{\text{Bayes}}{=} \frac{\overset{p_{A} = 0.7}{\mathbb{P}(E \mid A)} \cdot \overset{\frac{20}{100}}{\mathbb{P}(A)}}{\underset{\frac{41}{100}}{\mathbb{P}(E)}} \approx 34.15\%
$$
## 3. Determinare se gli eventi $E$ e $A$ sono [[indipendenza di due eventi|indipendenti]]

Vale l'identità $\mathbb{P}(A\cap B) = \mathbb{P}(A)\cdot \mathbb{P}(B)$ ?

- $\mathbb{P}(A)\cdot \mathbb{P}(B) = \frac{20 \cdot 41}{100}$
- $\mathbb{P}(A\cap B) = \mathbb{P}(E \mid A) \cdot \mathbb{P}(A) = \frac{70 \cdot 20}{100}$

L'identità non è verificata, quindi $A$ e $E$ non sono indipendenti.

## 4. Se $p_{B} = 0.4,\ p_{C} = 0.3$ determinare per quale valore di $p_{A}$ gli eventi $E$ ed $A$ sono indipendenti.

Abbiamo che

$E \perp \!\!\! \perp A \iff \underset{p_{A}}{\mathbb{P}(E \mid A)} = \underset{\frac{1}{100}(20 p_{A} + 30 p_{B} + 50 p_{C})}{\mathbb{P}(E)}$

Risolvendo $\mathbb{P}(E)$ con i dati conosciuti:

$$
p_{A} = \frac{1}{100}(20 p_{A} + 27) \to p_{A} = \frac{27}{80} \%
$$