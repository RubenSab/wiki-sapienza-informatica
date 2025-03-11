---
updated_at: 2025-03-11T20:16:56.081+01:00
---
#todo
# if else
## in C

``` c
if (x >= 0) {
	// codice da eseguire se il test è vero
} else {
	// codice da eseguire se il test è falso
}
// codice seguente

```

## in Assembly

```
.text
	# uso il registro t0 per la var. X
	bltz t0, Else                                # test X < 0

	# codice da eseguire se il test è vero
	j endif                                      # esco dall’IF

	Else:
		# codice da eseguire se il test è falso
	EndIf:
		# codice seguente
```

> `j` è l'istruzione di salto.
## esempio

```python
if i == j:
	f = g + h
else:
	f = g - h
```

```
addi s3, zero, i           # valore di i da inserire
addi s4, zero, j           # valore di j da inserire

bne s3, s4, Else         # vai a Else se i != j

add s0, s1, s2           # f = g + h (saltata se i != j)

j Esci                   # vai a Esci

Else: sub s0, s1, s2

Esci: # resto del codice
```
