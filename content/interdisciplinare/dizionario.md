---
updated_at: 2025-05-27T13:04:33.007+02:00
---
> Il dizionario è una [[struttura dati]] dinamica che prevede tre operazioni: **inserimento** di una coppia key-value, **ricerca** di una value in base alla key e **cancellazione** di una coppia key-value.

- Implementato con le [[hash table]], il costo delle operazioni sarà $O(n)$, il caso migliore sarà $\Theta(1)$ e il caso medio è $O(1)$.
- Implementato con gli [[albero di ricerca|alberi di ricerca]], il costo delle operazioni sarà $O(\log{n})$, il caso migliore sarà $\Theta(1)$, **ma non è garantito che il caso medio sia $O(1)$**.
# Implementazione con [[albero di ricerca]]

Con gli alberi, si può fare in modo che i nodi siano al massimo a distanza $O(\log(n))$ dalla radice.
Inoltre le chiavi dei nodi dell'albero di ricerca sono univoche ed è facile navigarci, quindi la ricerca di una valore da una chiave si può fare in $O(h)=O(\log{n})$.

# Implementazione con [[hash table]] (aperta)

``` python
class Nodo:
    def __init__(self, key, value = None, next = None):
        self.key = key
        self.value = value
        self.next = next


class LinkedList:

    def __init__(self):
        self.testa = None

    def get_nodo_da_chiave(self, key) -> Nodo:
        try:
            nodo = self.testa
            while nodo is not None:
                if nodo.key == key:
                    return nodo
                nodo = nodo.next
        except AttributeError:
            raise KeyError(f'la chiave {key} non è presente')

    def inserisci_pair(self, key, value=None) -> None:
        if not self.get_nodo_da_chiave(key):
            self.testa = Nodo(key, value, self.testa)

    def rimuovi_pair(self, key) -> None:
        if self.testa == None:
            raise KeyError(f'la chiave {key} non è presente')

        if self.testa.key == key:
            self.testa = self.testa.next
            return self.testa

        nodo = self.testa
        while nodo.next is not None:
            if nodo.next.key == key:
                nodo.next = nodo.next.next
                return self.testa
            nodo = nodo.next

        raise KeyError(f'la chiave {key} non è presente')    


class DizionarioHashAperto:

    def __init__(self, HASH_POSITIONS=100):
        self.HASH_POSITIONS = HASH_POSITIONS
        self.positions = [
            LinkedList() for _ in range(self.HASH_POSITIONS)
        ]

    def _my_hash(self, value) -> int:
        try:
            if type(value) is str:
                value = sum(ord(char) for char in value)
            return value % self.HASH_POSITIONS
        except TypeError:
            raise ValueError(f'il tipo {type(value).__name__} non è hashable dalla funzione my_hash')

    def __contains__(self, key: int) -> bool:
            nodo = self.positions[self._my_hash(key)].get_nodo_da_chiave(key)
            return bool(nodo)

    def __getitem__(self, key) -> int:
            return self.positions[self._my_hash(key)].get_nodo_da_chiave(key).value

    def __setitem__(self, key, value):
        self.rimuovi(key)
        self.inserisci(key, value)

    def inserisci(self, key, value=None) -> None:
        self.positions[self._my_hash(key)].inserisci_pair(key, value)

    def rimuovi(self, key: int) -> None:
        self.positions[self._my_hash(key)].rimuovi_pair(key)
```