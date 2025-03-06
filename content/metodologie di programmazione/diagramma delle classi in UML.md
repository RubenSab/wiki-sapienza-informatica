---
updated_at: 2025-03-06T14:14:36.331+01:00
---
> Un [[package]] si rappresenta come un rettangolo che all'interno può contenere [[classe|classi]] e altri metodi.

> Una [[classe]] si rappresenta come un rettangolo diviso orizzontalmente in tre sezioni: la prima contiene il titolo, la seconda contiene i campi nel formato `-campo:tipo_di_dati` e la terza contiene i metodi nel formato:
> `simbolo_della_visabilità metodo(campo:tipo_in_input,...):tipo_in_output`.

La visibilità si rappresenta così:
- `+` **visibilità pubblica**: ogni elemento che può accedere alla classe può anche accedere a ogni suo membro con visibilità pubblica
- `-` **visibilità privata**: solo le operazioni della classe possono accedere ai membri con visibilità privata
- `#` **visibilità protetta**: solo le operazioni appartenenti alla classe o ai suoi discendenti possono accedere ai membri con visibilità protetta
- `~` **visibilità package**: ogni elemento nello stesso package della classe (o suo sottopackage annidato) può accedere ai membri della classe con visibilità package.

- [[esempio di progettazione di una classe]]