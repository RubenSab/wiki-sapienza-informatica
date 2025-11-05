---
updated_at: 2025-11-03T22:23:44.533+01:00
---
Caso particolare: Dato un evento $A$ di cui è difficile calcolare la [[probabilità]], posso dividere l'[[evento]] $A$ in due eventi disgiunti ($B$ e $A-B = B^{C}$).

$$
A = (A \cap B) \cup (A \cap B^{C})
$$

Usando la [[probabilità condizionata]], si ricava che:

$$
\mathbb{P}(A)=\mathbb{P}(A \cap B) + \mathbb{P}(A \cap B^{C}) = \mathbb{P}(A \mid B)\cdot \mathbb{P}(B) + \mathbb{P}(A \mid B^{C}) \cdot \mathbb{P}(B^{C})
$$

# Esempio con esperimento a due fasi

È utile quando abbiamo un esperimento a due fasi.

Esempio: Lancio una moneta.
- Se esce $T$, lancio un dado.
- Se esce $C$, lancio 2 dadi.

Calcolare $\mathbb{P}(\text{la somma dei due numeri usciti è 6})$ (ricorda: se esce $T$ viene lanciato un solo dado)

Sia $B = \{\text{esce T}\},\quad B^{C} = \{\text{esce C}\}$

$$
\underset{\frac{1}{6}}{\mathbb{P}(A \mid B)} \cdot \underset{\frac{1}{2}}{\mathbb{P}(B)} + \underset{\frac{5}{36}}{\mathbb{P}(A | B^{C})} \cdot \underset{\frac{1}{2}}{\mathbb{P}(B^{C})} = \frac{11}{72}
$$
