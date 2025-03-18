---
updated_at: 2025-03-18T15:17:06.238+01:00
---
# if else

``` c
if (x >= 0) {
	// codice da eseguire se il test è vero
} else {
	// codice da eseguire se il test è falso
}
// codice seguente

```

Diventa

```
.text

	li t0, 5                                           # x = 5
	
	bge t0, zero, Else                                 # test x >= 0

	# codice da eseguire se il test è vero

	j EndIf                                            # esco dall’IF

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

# while e for

``` python
while i < 10:
	i += 1
```
## in Assembly

```
li t0, 1
li t1, 10

While:
	bge t0, t1, EndWhile
	addi t0, t0, 1
	j While

EndWhile:
	# parte del codice dopo il while
```

Un ciclo for è semplicemente un ciclo while con un contatore che si ferma a una certa soglia specificata