---
updated_at: 2025-10-14T17:14:50.945+02:00
---
> È l'operazione binaria che consente di selezionare le tuple del [[prodotto cartesiano]] dei due operandi he soddisfano una condizione del tipo $A\Theta B$, dove:

- $\Theta$ è un operatore di confronto
- $A$ è un attributo dello schema del primo operando
- $B$ è un attributo dello schema del secondo operando
- $\text{Dom(A)} = \text{Dom}(B)$

Osservazioni: $r1 \triangleright \triangleleft\ r2 = \rho_{A\Theta B}(r1\times r2)$
