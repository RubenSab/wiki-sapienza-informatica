---
updated_at: 2025-10-17T14:53:56.323+02:00
---
A volte è uguale invertire il [[probabilità condizionata|condizionamento]], se ad esempio $\mathbb{P}(A \mid B)$ è difficile da calcolare ma $\mathbb{P}(B \mid A)$ è facile.

> Il teorema dice che per due [[evento|eventi]] $A$ e $B$ si ha che $\mathbb{P}(A \mid B) = \frac{\mathbb{P}(B \mid A) \cdot \mathbb{P}(A)}{\mathbb{P}(B)}$, ora calcolando $\mathbb{P}(B)$ con la [[legge della probabilità totale]] otteniamo che

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
\mathbb{P}(A) = \underset{0.8}{\mathbb{P}(A \mid B)} \cdot \underset{0.3}{\mathbb{P}(B)} + \underset{0.25}{\mathbb{P}(A \mid B^{C})} \cdot \underset{0.7}{\mathbb{P}(B^{C})}
$$
Se invece avessimo chiesto:

> Incontrando Alice, e vediamo che ha l'ombrello. Qual è la probabilità che oggi il meteo preveda sole?

Basta riusare i dati precedenti e applicare il teorema di Bayes.

$$
\mathbb{P}(B^{C} \mid A) \underset{\text{Bayes}}{=} \frac{\mathbb{P}(B^{C} \cap A)}{\mathbb{P}(A)} = \frac{\mathbb{P}(A \mid B^{C}) \cdot \mathbb{P}(B^{C})}{\mathbb{P}(A)} = \frac{0.25 \cdot 0.7}{\underset{0.8}{\mathbb{P}(A \mid B)} \cdot \underset{0.3}{\mathbb{P}(B)} + \underset{0.25}{\mathbb{P}(A \mid B^{C})} \cdot \underset{0.7}{\mathbb{P}(B^{C})}} \approx 0.415
$$

# Esempio 2: falsi positivi

Contesto:

Un test per una mutazione genetica è accurato al $99\%$. Si sa che lo $0.5\%$ della popolazione ha la mutazione genetica.

```
- (B) mutazione (5/1000)
	- (A | B) positivo (99/100)
	- negativo (1/100)
- (B^C) assenza di mutazione (995/1000)
	- (B | A) positivo (99/100)
	- negativo (1/100)
```

> Fate il test, e esce positivo. Calcolare la probabilità che avete la mutazione genetica. $\mathbb{P}(B \mid A)$.

$$
\mathbb{P}(B \mid A) = \frac{\mathbb{P}(A \cap B)}{\mathbb{P}(A)}=\frac{\mathbb{P}(A \mid B)\cdot \mathbb{P}(B)}{\mathbb{P}(A)} = \frac{\mathbb{P}(A \mid B) \cdot \mathbb{P}(B)}{\mathbb{P}(A \mid B)\cdot \mathbb{P}(B) + \mathbb{P}(A \mid B^{C}) \cdot \mathbb{P}(B^{C})} = \frac{\frac{99}{100} \cdot \frac{5}{100}}{\frac{99}{100} \cdot \frac{5}{1000} + \frac{1}{100} \cdot \frac{995}{1000}} = 0.33
$$
