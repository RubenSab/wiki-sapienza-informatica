> Adder sequenziale che somma due numeri arbitrariamente lunghi sommando la cifra n-esima del primo con quella del secondo, producendo in output il singolo bit della somma delle due cifre a ogni iterazione.

# Sintesi dell'automa
## 1. [[automa a stati finiti (finite state automata)|Diagramma di Mealy]], stati dell'automa e della macchina

L'idea è di memorizzare il riporto generato in ogni iterazione in un singolo in un singolo [[flip-flop]], dato che è rappresentato da un singolo bit.

![[automa sommatore.png]]

Input: $a,\ b$
Output: $s$
Stati: 
- $q_{0}$ = riporto 0
- $q_{1}$ = riporto 1

|         | 00        | 01        | 10        | 11        |
| ------- | --------- | --------- | --------- | --------- |
| $q_{0}$ | $q_{0}/0$ | $q_{0}/1$ | $q_{0}/1$ | $q_{1}/0$ |
| $q_{1}$ | $q_{0}/1$ | $q_{1}/0$ | $q_{1}/0$ | $q_{1}/1$ |

## 2. tabella degli stati futuri realizzata con [[flip-flop delay (D)]]

| $a,\ b,\ q$ | $s$ | $q'$ (stato futuro) | $d$ |
| ----------- | --- | ------------------- | --- |
| 000         | 0   | 0                   | 0   |
| 001         | 1   | 0                   | 0   |
| 010         | 1   | 0                   | 0   |
| 011         | 0   | 1                   | 1   |
| 100         | 1   | 0                   | 1   |
| 101         | 0   | 1                   | 1   |
| 110         | 0   | 1                   | 1   |
| 111         | 1   | 1                   | 1   |
## 3. espressioni booleane dell'uscita e della funzione di eccitazione

Della somma:

| $a\ /\ b,q$ | 00  | 01  | 11  | 10  |
| ----------- | --- | --- | --- | --- |
| 0           | 0   | 1   | 0   | 1   |
| 1           | 1   | 0   | 1   | 0   |
$s=\overline{a}\cdot(b\oplus q)+a\cdot\overline{b\oplus q}=a\oplus b\oplus q$

Del flip-flop D:

| $a\ /\ b,q$ | 00  | 01  | 11  | 10  |
| ----------- | --- | --- | --- | --- |
| 0           | 0   | 0   | 1   | 0   |
| 1           | 0   | 1   | 1   | 1   |
$d=bq+aq+ab$

## 4. realizzazione

![[adder sequenziale.jpg]]