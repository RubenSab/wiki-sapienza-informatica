---
updated_at: 2025-11-15T18:30:39.345+01:00
---
> L'insieme di [[dipendenza funzionale|dipendenze funzionali]] $F^{A}$ è definito come l'insieme di tutte le dipendenze funzionali ottenute con gli *assiomi di Armstrong*.

# Assiomi di Armstrong

- se $f \in F$ allora $f \in F^{A}$
- **Assioma della [[proprietà, tipi di relazioni e ordini|riflessività]]**: se $Y \subseteq X \subseteq R$ allora $(X \to Y) \in F^{A}$
  Esempio: `ID` determina `Nome`, quindi `ID` determina `Nome, ID`.
- **Assioma dell'aumento**: se $(X \to Y) \in F^{A}$ allora $\forall Z \subseteq R\ ((XZ \to YZ) \in F^{A})$
  Esempio: `ID` determina `Nome`, quindi `ID, Cognome` determina `Nome, Cognome`.
- **Assioma della [[proprietà, tipi di relazioni e ordini#^7703c4|transitività]]**: se $(X \to Y) \in F^{A} \land (Y \to Z) \in F^{A}$ allora $(X \to Z) \in F^{A}$
  Esempio: `Specie` determina `Regno` e `Regno` determina `Phylum`, quindi `Specie` determina `Phylum`.

Dimostreremo che $F^{+} = F^{A}$, cioè che la chiusura di un insieme di dipendenze funzionali $F$ può essere ottenuta a partire da $F$ applicando ricorsivamente gli assiomi di Armstrong.

## Conseguenze

Da questi assiomi, derivano tre regole necessarie per derivare nuove dipendenze funzionali in $F^{A}$ da quelle già trovate in $F_{A}$, fino a trovarle tutte.

- **Regola dell'unione**: se $X \to Y \in F^{A}$ e $X \to Z\in F^{A}$ allora $X \to YZ \in F^{A}$
  Esempio: `ID` determina `Nome` e `ID` determina `Cognome`, quindi `ID` determina `Nome, Cognome`
- **Della decomposizione**: se $X \to Y \in F^{A}$ e $Z\subseteq Y$ allora $X \to Z\in F^{A}$
  Esempio: `ID` determina `Nome, Cognome`, quindi `ID` determina `Nome`.
- **Della pseudotransitività**: se $X \to Y \in F^{A}$ e $WY \to Z\in F^{A}$ allora $WX \to Z\in F^{A}$
  Esempio: Se `Matricola` determina `Facoltà` e `Facoltà, CodiceEsame` determina `Docente` allora `Matricola, CodiceEsame` determina `Docente`.

### Dimostrazioni

#### Regola dell'unione

- Se $X \to Y \in F^{A}$ allora $X \to XY \in F^{A}$ per aumento,
- se $X \to Z \in F^{A}$ allora $XY \to YZ \in F^{A}$ per aumento,
- dato che $X \to XY \to YZ \in F^{A}$, per transitività si ha che $X \to YZ \in F^{A}$.

#### Regola della decomposizione

- Se $Z\subseteq Y$ allora $Y \to Z\in F^{A}$ per riflessività,
- se $X \to Y \in F^{A}$ allora $X \to Y \to Z$, quindi $X \to Z$ per transitività.

#### Regola della pseudotransitività

- Se $X \to Y \in F^{A}$ allora $WX \to WY \in F^{A}$ per aumento,
- se $WY \to Z\in F^{A}$ allora $WX \to WY \to Z$, quindi $WX \to Z$ per transitività.

# Dimostrazione $F^{+} = F^{A}$

^9563ac

Per dimostrare che $F^{A} = F^{+}$ bisogna verificare sia che $F^{A} \subseteq F^{+}$ che $F^{+} \subseteq F^{A}$.

## 1. Dimostrazione $F^{A} \subseteq F^{+}$

Si può procedere per [[induzione]], incrementando di 1 a ogni passo il numero di applicazioni di assiomi di Armstrong.

- **Caso base** $i=0$: $X  \to Y \in F \implies X \to Y \in F^{+}$
- **Ipotesi induttiva** $i-1$:   $f \in F^{A(i-1)} \implies f \in F^{+}$ (assumiamo che tutte le dipendenze $f$ prodotte nel passo $i-1$ e nei passi precedenti sono soddisfatte da ogni istanza legale)
- **Passo induttivo**: Per l’ipotesi induttiva ogni dipendenza funzionale ottenuta a partire da $F$ applicando gli assiomi di Armstrong un numero di volte minore o uguale a $i-1$ è in $F^{+}$. Dobbiamo dimostrarlo per un numero di volte uguale a $i$. Si possono presentare tre casi:

	1. Se $X \to Y \in F^{A(i)}$ è stata ottenuta per **riflessività**, allora $Y \subseteq X$. $\forall r\ \text{legale}\ t_{1}[X]=t_{2}[X] \implies t_{1}[Y] = t_{2}[Y]$, quindi $X \to Y \in F^{+}$
	2. Se $X \to Y \in F^{A(i)}$ è stata ottenuta per **aumento** da una dipendenza funzionale $V \to W \in F^{A(i-1)}$, quindi $X = VZ$ e $Y = WZ$ per qualche insieme di attributi $Z\subseteq R$. $\forall r\ \text{legale}\ t_{1}[X] = t_{2}[X] \implies t_{1}[V] = t_{2}[V] \land t_{1}[Z] = t_{2}[Z]$. Per ipotesi induttiva ($V \to W \in F^{A(i-1)}$) da $t_{1}[V] = t_{2}[V]$ segue $t_{1}[W]=t_{2}[W]$, infine da $t_{1}[W]=t_{2}[W] \land t_{1}[Z] = t_{2}[Z]$ segue $t_{1}[Y] = t_{2}[Y]$. 
	3. Se $X \to Y \in F^{A(i)}$ è stata ottenuta per **transitività** a due dipendenze funzionali $X \to Z$ e $Z\to Y \in F^{A(i-1)}$. $\forall r\ \text{legale}\ t_{1}[X] = t_{2}[X]$. Per ipotesi induttiva ($X \to Y \in F^{A(i)}$), da $t_{1}[X] = t_{2}[X]$ segue $t_{1}[Z]=t_{2}[Z]$, da $t_{1}[Z] = t_{2}[Z]$ segue $t_{1}[Y] = t_{2}[Y]$.

Abbiamo dimostrato che $F^{A} \subseteq F^{+}$.

## 2. Dimostrazione $F^{+} \subseteq F^{A}$

Supponiamo per assurdo che esista una dipendenza funzionale $X \to Y \in F^{+} \land X \to Y \notin F^{A}$.

Studiamo una particolare istanza $r$ di $R$ (ma senza perdita di generalità) per incontrare una contraddizione, dimostrando che $X \to Y \in F^{+} \implies X \to Y \in F^{A}$.

L'istanza studiata ha solo due tuple, **uguali** sugli attributi $X^{+}$ (la [[chiusura di un insieme di attributi]] $X$) e **diverse** su $R-X^{+}$ cioè tutti i rimanenti.

### Prima parte: $r$ è un'istanza legale

Sia $V \to W \in F$ una dipendenza funzionale qualsiasi in $r$ e supponiamo per assurdo che non sia soddisfatta da $r$, quindi che $r$ non sia legale.
Se così fosse, le due tuple di $r$ dovrebbero avere gli stessi valori per $V$ e diversi valori per $W$, in modo che $V$ non determini $W$.

Ciò implica che $V \subset X^{+}$ (i valori uguali tra le due tuple) e $W \cap (R-X^{+}) \neq \emptyset$ (almeno qualche attributo nell'insieme $W$ è diverso tra le due tuple).

$V \subset X^{+} \implies X \to V \in F^{A}$ per il [[chiusura di un insieme di attributi#^aff93b|lemma della chiusura di un insieme di attributi]].

Abbiamo $V \to W \in F$ e $X \to V \in F^{A}$, quindi per transitività $X \to W \in F^{A}$.

Sempre per il lemma della chiusura, stavolta applicato nel senso opposto, $X \to W \in F^{A} \implies W \subseteq X^{+}$, che **contraddice** $W \cap (R-X^{+}) \neq 0$; quindi, tornando alla premessa iniziale, $r$ è legale.

### Seconda parte

inizialmente abbiamo supposto per assurdo che $X \to Y \in F^{+} \land X \to Y \notin F^{A}$, poi abbiamo mostrato che $r$ (come definita) è un'istanza legale, quindi $r$ soddisfa $X \to Y$.

Ricordiamo che per definizione le due tuple sono uguali su $X^{+}$, quindi per il lemma coincidono sugli attributi $X$ e quindi visto che $X \to Y$, allora devono anche coincidere su $Y$. Perciò $Y$ è nella chiusura di $X$ ($Y \subseteq X^{+}$) e per il lemma vale $X \to Y \in F^{A}$, contraddicendo la premessa iniziale. $\square$

# Implementazione in Python del calcolo "manuale" della chiusura di Armstrong

``` python
from itertools import chain, combinations

def powerset(iterable):
    s = list(iterable)
    return chain.from_iterable(combinations(s, r) for r in range(len(s)+1))


class Dependency:
    def __init__(self, determinant: set, determined: set):
        self.determinant = determinant
        self.determined = determined

    def __repr__(self):
        return (f"{self.determinant} -> {self.determined}")

    def __eq__(self, other: Dependency):
        if self.determinant == other.determinant and \
        self.determined == other.determined:
            return True
        return False

    def __hash__(self):
        return hash((frozenset(self.determinant), frozenset(self.determined)))

    def is_trivial(self):
        return self.determined.issubset(self.determinant)

    def augment(self, attribute: set) -> Dependency:
        if isinstance(attribute, str):
            attribute = {attribute}
        return Dependency(
            self.determinant | attribute,
            self.determined | attribute
        )

    def reflexivity(self) -> set[Dependency]:
        return {
            Dependency(self.determinant, set(subset))
            for subset in powerset(self.determinant) if subset
        }

    def transitivity(self, other: Dependency) -> Dependency:
        if self.determined == other.determinant:
            return Dependency(self.determinant, other.determined)
        else:
            return self

class RelationScheme:
    def __init__(self, attributes: set, dependencies: set[dependencies]):
        self.attributes = attributes
        self.dependencies = dependencies

    def __repr__(self):
        return '\n'.join({str(d) for d in self.dependencies})

    def apply_augment(self) -> None:
        new_dependencies = {
            d.augment(a)
            for d in self.dependencies
            for a in self.attributes
        }
        self.dependencies |= new_dependencies

    def apply_reflexivity(self) -> None:
        new_dependencies = {
            reflexive_dep 
            for d in self.dependencies 
            for reflexive_dep in d.reflexivity()
        }
        self.dependencies |= new_dependencies

    def apply_transitivity(self) -> None:
        new_dependencies = {
            d1.transitivity(d2)
            for d1 in self.dependencies
            for d2 in self.dependencies
        }
        self.dependencies |= new_dependencies

    def armstrong_closure(self) -> None:
        prev_n = 0
        while prev_n < len(self.dependencies):
            prev_n = len(self.dependencies)
            self.apply_reflexivity()
            self.apply_augment()
            self.apply_transitivity()

    def filter_non_trivials(self) -> None:
        self.dependencies = {d for d in self.dependencies if not d.is_trivial()}
```

Esempio:

``` python
r = RelationScheme(
    {"CodiceFiscale", "Nome", "Cognome", "Città", "Regione"},
    {
        Dependency({"CodiceFiscale"}, {"Nome", "Cognome", "Provincia"}),
        Dependency({"Provincia"}, {"Regione"}),
    }
)

r.armstrong_closure()
r.filter_non_trivials()
print(r)
print(len(r.dependencies))
```

Produce 560 dipendenze funzionali, di cui 192 banali.