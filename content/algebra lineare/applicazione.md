---
updated_at: 2025-10-01T15:49:59.623+02:00
---
> Una [[corrispondenza]] $f=(X, Y, \Gamma)$ ($X$ = dominio, $Y$ = codominio, $\Gamma$ = grafo da $X$ a $Y$) si dice [[applicazione]] se $\forall a \in X,\ \exists !\ b \in Y : (a, b) \in \Gamma$ si dice che $b = f(a)$ e si scrive anche $X \xrightarrow{f} Y$ (applicazione $f$ da $X$ a $Y$).

È un sinonimo di [[funzione]] e di mappa.

Un'applicazione $X \xrightarrow{f} Y$ si dice:

- **iniettiva** se:
	- $\forall x, x' \in X\ (f(x) = f(x') \implies x = x')$;
	- alternativamente è iniettiva se $\forall y \in Y(\ f^{-1}(\{y\})=\emptyset \lor f^{-1}(\{y\})\ )$ è un singleton; (se ogni elemento del codominio ha una sola "freccia entrante");
	- alternativamente è iniettiva se $\text{Card}(f^{-1}(\{y\})) \leq 1$.

- **suriettiva** se:
	- $\forall y \in Y\ \exists x \in X : f(x) = y$ (tutti gli elementi del codominio hanno "frecce entranti");
	- alternativamente $f$ è suriettiva se $\forall y \in Y, f^{-1}(\{y\}) \neq \emptyset$;
	- alternativamente $f$ è suriettiva se $f(X) = Y$ (non un sottoinsieme di $Y$).

- **biettiva** se:
	- è sia suriettiva che iniettiva;
	- alternativamente se e solo se $\forall y \in Y$, $f^{-1}(\{y\})$ è un singleton;
	- è l'applicazione che ha $\Delta_{x}$ come grafo (definizione quasi inutile, solo per curiosità).

> Se $f$ è **iniettiva**, scrivo $X \rightarrowtail Y$, se $f$ è **suriettiva**, scrivo $X \twoheadrightarrow Y$.