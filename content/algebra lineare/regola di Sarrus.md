---
updated_at: 2026-01-14T13:36:14.593+01:00
---
> È uno strumento mnemonico per calcolare il [[determinante]] delle [[spazio vettoriale di matrici|matrici]] $3\times 3$.

Si applica accostando le prime due colonne della matrice a sinistra della matrice stessa, costruendo una matrice $3 \times 5$. Poi si calcolano i prodotti degli elementi sulle diagonali e si sommano o sottraggono come in figura.

![[Pasted image 20260114133410.png]]

$$
\det\left(\begin{pmatrix} a & b & c \\ d & e & f \\ g & h & i \end{pmatrix}\right) = aei + bfg + cdh - gec - hfa - idb
$$