---
updated_at: 2026-09-24T11:58:58.506+02:00
---
# Esempio estremo di come la pragmatica può essere ambigua

``` c
int main(void) {
	int i = 1;
	char *c = &i;
	printf("%d", *c);
}
```

Non stampa sempre 1 su tutte le architetture, ma si comporta diversamente sui sistemi little o big-endian.

`c` e `i` [[puntatore|puntano]] alla stessa locazione, e 1 è rappresentato nella [[memoria]] come vari zeri e un uno in ogni sistema, però alcuni sistemi sono big-endian e altri little-endian.

- Se il sistema è big-endian (1 = `10000000...")`, allora l'uno (*intero*) verrà troncato al prefisso `10000000` (1) quando verrà stampato come *carattere*.
- Se il sistema è little-endian (1 = `00000000...00001")`, allora l'uno (*intero*) verrà troncato al prefisso `00000000` (0) quando verrà stampato come *carattere*.
