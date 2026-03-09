---
updated_at: 2026-03-09T23:19:44.749+01:00
---
# Metodo naive

Per verificare se un [[grafo]] diretto ha un pozzo universale, si può fare una ricerca esaustiva, controllando se ogni nodo sia un pozzo universale o meno, fermandosi appena lo si è trovato.

La [[complessità temporale]] è $O(n^{2})$ perché nel caso peggiore si eseguono $2n$ controlli per $n$ nodi.

# Ricerca ottima

Usando le [[implementazioni dei grafi|matrici di appartenenza]] si può osservare che

- se `matrice[riga][colonna]` è 1, il nodo `riga` non può essere un pozzo universale, 
- se `matrice[riga][colonna]` è 0, il nodo `colonna` non può essere un pozzo universale. #todo fact check

#todo inserisci algoritmo