---
updated_at: 2025-03-18T10:57:44.472+01:00
---
# istruzioni condizionali
## if

``` java
if (<espressione booleana>) <singola istruzione>;
```

Oppure
``` java
if (<espressione booleana>)
{
	<istruzioni>;
}
```

## if else

``` java
if (<espressione booleana>) <caso true>;
else                        <caso false>;
```

Oppure

``` java
if (<espressione booleana>)
{
	<caso true>;
}
else
{
	<caso false>;
}
```

> N.B.: esiste il problema dell'**else sospeso**

### ambiguità dell'else sospeso

``` java
if (<condizione1>)
	if (<condizione2>)
		<istruzioneA>
else
	<istruzioneB>
```

> N.B.: Dato che non ci sono le graffe per disambiguare, non è ovvio se l'else si riferirà al primo o al secondo if, infatti il compilatore lo assocerà sbagliando all'if più vicino (
> `<condizione2>`).

## if else multiplo

``` java
if <condizione1>: <istruzione1>;
else if <condizione2>: <istruzione2>;
else if <condizione3>: <istruzione3>;
else if <condizioneN>: <istruzioneN>;
```

## operatore condizionale (Elvis notation 🕺)

``` java
<condizione> ? <valore caso vero> : <valore caso falso>;
```

Esempi:

``` java
int abs = x < 0 ? -x : x;

int max = x > y ? x : y;

String testaCroce = Math.random() < 0.5 ? "Testa" : "Croce";
```

## switch case

``` java
switch(<espressione intera con risultato intero, char compresi>)
{
	case <risultato dell espressione numero 0>: <istruzione0>; break;
	case <risultato dell espressione numero 1>: <istruzione1>; break;
	case <risultato dell espressione numero 2>: <istruzione2>; break;
	case <risultato dell espressione numero N>: <istruzioneN>; break;
	default: <istruzione da eseguire se il caso non è tra i precedenti>; break;
}
```

## switch compatti

``` java
switch(<espressione intera con risultato intero, char compresi>)
{
	case <risultato dell espressione numero 0> -> <istruzione0>;
	case <risultato dell espressione numero 1> -> <istruzione1>;
	case <risultato dell espressione numero 2> -> <istruzione2>;
	case <risultato dell espressione numero N> -> <istruzioneN>;
	default -> <istruzione da eseguire se il caso non è tra i precedenti>;
}
```

> N.B.: L'operatore freccia sottintende il break.

## espressione switch

Esempio: #todo 

``` java
String s = switch(c) {
	case 'k' -> "kappa";
	case 'h' -> "acca";
	case 'e' -> "elle";
	case 'c' -> "ci";
	case 'a', 'e', 'i', 'o', 'u' -> 
}
```

# cicli

## while

``` java
while (<espressione booleana>) <singola istruzione>;

```

``` java
while (<espressione booleana>)
{
	<istruzioni>;
}
```

> N.B.: l'espressione booleana può svolgere due compiti insieme: controllare se la condizione del ciclo si verifica e incrementare/decrementare grazie al [[operatori|post incremento o decremento]]:

Esempio:

``` java
public static String getLinea(int k)
{
	String s = "";
	while (k-- > 0) s += "*";
	return s;
}
```

## do while

``` java
do
{
	<istruzioni>;
}
while (<espressione booleana>)
```

## for

``` java
for (<inizializzazione>; <espressione booleana>; <incremento>)	<singola istruzione>;
```

``` java
for (<inizializzazione>; <espressione booleana>; <incremento>)
{
	<istruzioni>;
}
```

equivale a

``` java
<inizializzazione>
while (<espressione booleana>)
{
	<istruzioni>;
	<incremento>;
}
```

``` java
for (int i=0, i<=10, i+=3) {...} /* l'incremento non è necessariamente unitario*/

for (int i=10, i>0, i--) {...} /* la variabile di controllo non deve essere necessariamente crescente */

for (int k=0, i=0, i<=10; i++, k+=5) {...} /* Le istruzioni di inizializzazione e incremento possono riferirsi a più variabili */
```

## break

> Indipendentemente dal tipo di ciclo (while, do...while, for), può essere necessario uscire dal ciclo durante l’esecuzione del suo corpo.

- L’istruzione break permette di uscire solo dal ciclo corrente se non si specifica un’etichetta, quindi come fare nel caso in cui si voglia uscire da una sequenza di cicli annidati?
- Si può specificare un’etichetta prima di un ciclo e uscire da quel ciclo con break \<etichetta\>

![[Pasted image 20250318092548.png]]