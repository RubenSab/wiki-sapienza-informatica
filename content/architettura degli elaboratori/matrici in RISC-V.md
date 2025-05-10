---
updated_at: 2025-04-15T11:47:36.716+02:00
---
``` python
matrix = [
	[1,2,3]
	[4,5,6]
	[7,8,9]
]
```

Dato che in assembly lo spazio di memoria è lineare, le matrici (come le altre [[struttura dati]]) non possono esistere fisicamente, ma sono da pensare come un'[[array]] di dati su cui è definita una procedura per ottenere l'elemento agli indici x e y corrispondenti come se fosse una matrice.

```
.data
	matrice: .word 1, 2, 3, 4, 5, 6, 7, 8, 9
	width: .word 3

.text

	li t0, 2 # indice x
	li t1, 1 # indice y
	
	li t2, 4 # carico 4 in t2
	lw t3, width # carico la larghezza della matrice in t3
	
	mul t4, t3, t1 # t4 = larghezza * indice y
	add t4, t4, t0 # t4 = larghezza * indice y + indice x
	mul t4, t4, t2 # t4 = 4 * (larghezza * indice y + indice x)
	
	
	la t5, matrice # carico l'indirizzo base della matrice in t5
	add t4, t4, t5 # incremento t4 di t5
	
	lw t6, (t4) # carico il valore memorizzato all'indirizzo di memoria t4 in t6
```