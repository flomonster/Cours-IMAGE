---
title: "ADONNEE"
date: "20-2-2019"
link: "https://hackmd.io/ZPaeRYHVQG2_eqqvSRVKKw#"
tags: SCIA, IMAGE, MTI, GISTRE, cours
---

# Analyse des données

![Pres](http://www.lespetitslapins.fr/wp-content/uploads/2011/01/lapinblanc2.jpg)

## Description bidimensionelle et mesure de liaison entre variables


### Couples de variables aléatoires

Soit 2 variables aléatoires $X$ et $Y$ (dans le cas discret) définies sur un espace probabilisé $(\Omega, \mathscr{C}, \mathbb{P})$

* $\Omega$ Univers (l'ensemble des éléments élémentaires)
* $\mathscr{C}$ attribu tel que $\mathscr{C}$ inclu dans $P(\Omega)$ (== "toutes les parties de Omega")
* $\mathbb{P}$ probabilité

**Exemple :**
> Un évènement $A$ = $\{ (i,j) / i\} + j \ge 10$,
> $\mathscr{C} \in P$

$X(\omega)= \{X_i ~/~ i \in I \}$ l'ensemble des valeurs de X
$Y(\omega)= \{ Y_j ~/~ j \in J \}$ l'ensemble des valeurs de Y

#### Loi conjointe $(X,Y)$

:::success
Définition :
On appelle loi conjointe du couple $(X,Y)$ l'ensemble des couples $((X_i, Y_j), P_{i,j})$ avec $\forall x_i \in X_\omega$, $\forall y_i \in Y_{\omega}$
$$P_{i,j}=\mathbb{P}((X=x_i)\cap(Y=y_i))$$
$P_{i,j} \geqslant 0$ et $\displaystyle\sum_{i,j}P_{i,j}=1$
:::

:::info
Remarque :
$I=[[1,r]]$, $J=[[1,s]]$
$$
\begin{bmatrix}
       & y_1 & \dots & y_j & \dots & y_s & \text{Loi de X}\\
x_1    & P_{1,1}   &       & \vdots    &       & P_{1,s} & P_{1,\cdot}   \\
\vdots &     &       &  \vdots   &    &    & \vdots \\
x_i    & \dots & \dots & \boxed{P_{i,j}} &       &  & P_{i,\cdot}   \\
\vdots &     &       &     &       & & \vdots    \\
x_r    & P_{r,1}    &       &     &       & P_{r,s}  & P_{r,\cdot}  \\
\hline \\
\text{Loi de Y} & P_{\cdot,1} & \dots & P_{\cdot,j} & \dots & P_{\cdot,s} &  1\\
\end{bmatrix}
$$
:::

#### Lois marginales
"comment déterminer la loi de X prise séparemment blabla loi de Y" --> pas compris


Les V.A. $X,Y$ sont appelees variables marginales des couples $(X,Y)$

Loi marginale de X :
$$\boxed{\mathbb{P} [X = x_i] =  P_{i.}  = \sum_{j \in J} P_{i,j}}$$

Loi marginale de Y :
$$\boxed{\mathbb{P} [Y = y_j] =  P_{.j}  = \sum_{i \in I} P_{i,j}}$$


**Exemple :**

$$\begin{bmatrix}
                  & 1             &       2       &        3      &       4      & \text{Loi de X} \\
1                 & \frac{1}{16}  & \frac{1}{16}  &  \frac{1}{16} & \frac{1}{16} & \frac{1}{4} \\
2                 & 0             & \frac{2}{16}  &  \frac{1}{16} & \frac{1}{16} & \frac{1}{4} \\
3                 & 0             & 0             &  \frac{3}{16} & \frac{1}{16} & \frac 1 4\\
4                 & 0             & 0             & 0             & \frac{4}{16} & \frac 1 4\\
\text{Loi de Y}   & \frac{1}{16}  & \frac{3}{16}  & \frac{5}{16}  & \frac{7}{16} & 1\\
\end{bmatrix}
$$


#### Lois conditionnelles


On appelle loi conditionnelle de $X = x_i$ sachant que $Y = y_j$ :

:::success
$$\mathbb{P}(X = x_i / Y = y_j) = \frac{\mathbb{P}((X = x_i) \cap (Y = y_i))}{\mathbb{P}(Y = y_j)} = \frac{\mathbb{P_{ij}}}{\mathbb{P}_{.j}}$$
avec $\mathbb{P}(Y = y_j) \ne 0$
:::

:::success
$$\mathbb{P}(X=x_i / Y = y_j)=\frac{\mathbb{P}_{i,j}}{\mathbb{P}_j}$$
$$\mathbb{P}(Y=y_j / X = x_i)=\frac{\mathbb{P}_{i,j}}{\mathbb{P}_i}$$
:::

**Exemple :** (matrice précédente)

$\mathbb{P}(X=x_i / y=3)$

| $X_i$                   | 1             | 2             | 3             | 4  |
| :---------------------: | ------------- | ------------- | ------------- | -- |
| $\mathbb{P}(X=x_i/Y=3)$ | $\frac{1}{5}$ | $\frac{1}{5}$ | $\frac{3}{5}$ | 0  |

$$\mathbb{P}(X=1/Y=3)=\frac{\mathbb{P}((X=1) \cap (Y=3))}{\mathbb{P}(Y=3)}=\frac{\frac{1}{16}}{\frac{5}{16}}=\frac{1}{5}$$

:::success
Définition : [Indépendance]
$X$ et $Y$ sont indépendantes ssi $$\mathbb{P}(X = x_i) \cap \mathbb{P}(Y = y_j) = \mathbb{P}(X=x_i) \cdot \mathbb{P}(Y=y_j) $$
$\forall x_i\in X(\omega)$, $\forall y_j \in Y(\omega)$
:::

#### Loi d'une fonction de 2 variables

Soit $g : \mathbb{R}^2 \longmapsto \mathbb{R}$ et $Z$ la variable aléatoire $Z = g(X,Y)$ avec $(X,Y)$ couple de valeurs aléatoires
$g$ est une fonction quelconque.

Les valeurs prises par $Z: g(x_i, y_j)$, $X_i\in X(\omega)$, $Y_j\in Y(\omega)$

$$Z(\omega) = \{ Z_k ~/~ k \in K \}_{K \subset \mathbb{N} \text{ ou } \mathbb{Z}}$$

$$\underbrace{[Z = Z_k]}_{\text{événement }} = \bigcup_{(i,j)} ([X=x_i]\cap [Y=y_j])$$


:::info
Evènements incompatibles : leur intersection est vide.
Soit $A_{i,j} \bigcap A_{i',j'} = \emptyset \\ (i,j) \ne (i',j')$
:::

:::success
$$\mathbb{P}(Z=Z_k)=\sum_{(i,j) ~/~ g(X)_{ij}=Z_k} \mathbb{P}((X=x_i)\cap (Y=y_j))$$
:::

:::info
Remarque :
En particulier $Z=X+Y$
$$\mathbb{P}(Z=x+y)=\sum_{x+y=Z}\mathbb{P}((X=x)\cap(Y=y))$$
Si $Z = X \cdot Y$
$$\mathbb{P}(Z=x\cdot y)=\sum_{xy=Z}\mathbb{P}((X=x)\cap(Y=y))$$
:::

**Exemple :**


| X\Y   |  1             | 2              | 3              | 4              |
| :---: | :------------: | :------------: | :------------: | :------------: |
| 1     | $\frac{1}{16}$ | $\frac{1}{16}$ | $\frac{1}{16}$ | $\frac{1}{16}$ |
| 2     | 0              | $\frac{1}{8}$  | $\frac{1}{16}$ | $\frac{1}{16}$ |
| 3     | 0              | 0              | $\frac{3}{16}$ | $\frac{1}{16}$ |
| 4     | 0              | 0              |  0             | $\frac{4}{16}$ |

1 Déterminer la loi de $S = X + Y$
2 Déterminer la loi de $P = X \cdot Y$

$S(\omega) = \{2, 3, 4,5,6,7,8 \}$


| $S_i$ | 2  | 3  | 4  | 5  | 6  | 7  | 8  |
| :---: | -- | -- | -- | -- | -- | -- | -- |
| $P_i=P(S=S_i)$ | $\frac{1}{16}$ | $\frac{1}{16}$ | $\frac{3}{16}$ | $\frac{2}{16}$ | $\frac{4}{16}$ | $\frac1{16}$ |$\frac4{16}$ |

$P= X \cdot Y$ (produits)

$p(\omega) = \{1,2,3,4,6,8,9,12,16\}$


| $P_i$ | 1  | 2  | 3  | 4  |  6 | 8  | 9  | 12 | 16 |
| :---: | -- | -- | -- | -- | -- | -- | -- | -- | -- |
| $\mathbb{P}(P=P_i)$ | $\frac{1}{16}$ | $\frac{1}{16}$ | $\frac{1}{16}$ | $\frac{3}{16}$ | $\frac{1}{16}$ | $\frac1{16}$ |$\frac3{16}$ | $\frac{1}{16}$ | $\frac{4}{16}$ |

Espérance de $Z$ = $g(X,Y)$

:::success
**Definition :**
Soit $Z = g(X,Y)$
On appelle esperance de $Z$
$$E(Z)=\sum_{i\in I \\ j \in J} (g(x_i, y_j) \cdot \mathbb{P}((X=x_i)\cap (Y=y_i)))$$
:::

:::info
**Remarque :**
$$E(XY) = \sum_i \sum_j x_iy_j \mathbb{P}_{i,j}$$
Si 2 V.A. $X$ et $Y$ sont indépendantes alors $$E(X,Y)=E(X)E(Y)$$

* Reciproque est fausse en général
* Condition suffisante non necessaire


**Contre-exemple :**
| X\Y      | 0               | 1             | 2             | Loi de X       |
| :------: | :-------------: | :-----------: | :-----------: | :------------: |
| 0        | $\frac{1}{20}$  | $\frac{1}{4}$ | 0             | $\frac{3}{10}$ |
| 1        | $\frac{17}{60}$ | $\frac{1}{4}$ | $\frac{1}{6}$ | $\frac{7}{10}$ |
| Loi de Y | $\frac{1}{3}$   | $\frac{1}{2}$ | $\frac{1}{6}$ | 1              |

$$E(X \cdot Y) = \sum_{i = 0}^1\sum^2_{j = 0} i \cdot j ~ P_{i,j} = \frac{1}{4} \times 1 + \frac{1}{6} \times 2$$

$E(X)=\displaystyle\sum_{i=0}^{1}i~P_i=\frac{7}{10}$
$E(Y)=\displaystyle\sum_{j=0}^{2}j~P_j=\frac 1 2 + \frac 2 6=\frac{5}{6}$

$E(X)E(Y)=\frac{35}{60}=\frac{7}{12}=E(XY)$
$E(X \cdot Y)=E(X)E(Y)$
Mais $X$ et $Y$ sont dépendantes car $\mathbb{P}((X=0)\cap(Y=2))=0\neq \mathbb{P}((X=0)\mathbb{P}(Y=2))=\frac{1}{20}$
:::

:::success
**Définition : [Covariance]**
Soit 2 V.A. $X$,$Y$ discrétes
On appelle covariance de x,y l'espérance de xy - le produit des espérances respectives.
$$Cov(X,Y)=E(XY)-E(X)E(Y)$$
$$V(X + Y) = V(X) + V(Y) + 2Cov(X + Y)$$
Si $X$ et $Y$ sont indépendantes $\Longrightarrow Cov(X,Y)=0$
$\boxed{V(X+Y) = V(X) + V(Y)}$
:::

#### Corrélation linéaire

:::success
**Défintion :**
On appelle coefficient de corrélation entre $X$ et $Y$,
\begin{align}
\rho(X,Y)&=\frac{Cov(X,Y)}{\sigma_x \sigma_y}\\
\underbrace{\sigma_X}_{\text{écart-type}} &= \sqrt{V(X)}, \sigma_Y = \sqrt{V(Y)}
\end{align}
:::

:::info
**Remarque :**
* $\sigma_x = ||X-E(X)|| \text{ , } \sigma_y = ||Y-E(Y)||$
* $\underbrace{\langle X\_E(X), Y\_E(Y) \rangle}_{produit scalaire} = Cov(X,Y)$
* $\rho(X,Y)=\frac{\langle X-E(X), Y-E(Y)\rangle}{||X-E(X)||||Y_E(Y)||}$
* $\cos \theta = \frac{\langle u,v\rangle}{||u||||v||}$
* $|\rho(X,Y)| \leqslant 1$
* $|\rho(X,Y)| = 1$ -> $X, V$ colinéaire
* $|\rho(X,Y)| = 0$ -> $X, V$ perpendiculaire
:::

> **Exercice d'application :**
> "A preparer pour la prochaine fois" :
>
> | x_i          | -2        | -1        | 0         | 1         | 2         |
> | --          | -- | --        | --         | --         | --        |
> | $P(X = X_i)$ | $\frac16$ | $\frac14$ | $\frac 1 6$ | $\frac14$ | $\frac16$ |
>
> 1. Donner la loi conjointe de $(X,Y)$
> 2. Loi marginale de Ya
> 3. Indépendance?
> 3. Calculer $Cov(X,Y)$
>
## Description multidimensionnelle

### Tableau de données

### Matrice de poids

### Centre de gravité

### Matrice de variance

### Covariance et matrice de corrélation

### Espace des individus et espace des variables

### Methode ACP
Il est au bon endroit ce paragraphe ?
:::info
Méthode ACP = Analyse Composante Principale
On a une matrice
$P$ variables (colonnes)
$n$ Individus (lignes) : population de pressions, vitesses, objets, habitants...
Un élément de la matrice $i,j =$ valeur de $P_j$ pour l'individu $i$
:::

:::info
[**Inertie**](http://jybaudot.fr/Stats/inertie.html) : moyenne des distances au carré des points au [**Barycentre**](https://fr.wikipedia.org/wiki/Barycentre).
:::

#### Axe factoriels

#### Composantes principales

#### Corrélation linéaire
