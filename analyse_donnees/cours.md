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
$$P_{i,j}=\mathbb{P}((X=x_i)\cap(Y=y_j))$$
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
$$\mathbb{P}(X=x_i / Y = y_j)=\frac{\mathbb{P}_{i,j}}{\mathbb{P}_{.j}}$$
$$\mathbb{P}(Y=y_j / X = x_i)=\frac{\mathbb{P}_{i,j}}{\mathbb{P}_{i.}}$$
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

Equivalent à : 
$$\mathbb{P}_{i,j} = \mathbb{P}_{i.} \cdot \mathbb{P}_{.j} $$
:::

#### Loi d'une fonction de 2 variables

Soit $g : \mathbb{R}^2 \longmapsto \mathbb{R}$ et $Z$ la variable aléatoire $Z = g(X,Y)$ avec $(X,Y)$ couple de valeurs aléatoires, 
$g$ est une fonction quelconque.

Les valeurs prises par $Z: g(x_i, y_j)$, $X_i\in X(\omega)$, $Y_j\in Y(\omega)$

$$Z(\omega) = \{ Z_k ~/~ k \in K \}_{K \subset \mathbb{N} \text{ ou } \mathbb{Z}}$$

$$\underbrace{[Z = z_k]}_{\text{événement }} = \bigcup_{(i,j)} ([X=x_i]\cap [Y=y_j])$$


:::info
Evènements incompatibles : leur intersection est vide.
Soit $A_{i,j} \bigcap A_{i',j'} = \emptyset \\ (i,j) \ne (i',j')$
:::

:::success
$$\mathbb{P}(Z=z_k)=\sum_{(i,j) ~/~ g(X)_{ij}=Z_k} \mathbb{P}((X=x_i)\cap (Y=y_j))$$
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
* $\underbrace{\langle X\_E(X), Y\_E(Y) \rangle}_{\text{produit scalaire}} = Cov(X,Y)$
* $\rho(X,Y)=\frac{\langle X-E(X), Y-E(Y)\rangle}{||X-E(X)||||Y_E(Y)||}$
* $\cos \theta = \frac{\langle u,v\rangle}{||u||||v||}$
* $|\rho(X,Y)| \leqslant 1$
* $|\rho(X,Y)| = 1 \longrightarrow X, V$ colinéaire
* $|\rho(X,Y)| = 0 \longrightarrow X, V$ perpendiculaire
:::

> **Exercice d'application :**
> "A preparer pour la prochaine fois" :
>
> | $X_i$          | -2        | -1        | 0         | 1         | 2         |
> | --          | -- | --        | --         | --         | --        |
> | $\mathbb P(X = X_i)$ | $\frac16$ | $\frac14$ | $\frac 1 6$ | $\frac14$ | $\frac16$ | 
>
> 1. Donner la loi conjointe de $(X,Y)$
> 2. Loi marginale de Y
> 3. Indépendance?
> 3. Calculer $Cov(X,Y)$
> ---
> **La  loi conjointe de $(X,Y)$**
> * $P_{i,j} = \mathbb P((X=i) \cap (Y=j)) = 0$ si $j \neq i^2$
> * $P_{i,j} = \mathbb P(\underbrace{(X=i) \cap (Y=i^2)}_{\{X=i\} \subset \{Y=i^ 2\}}) = \mathbb P(X=i)$ si $j \neq i^2$
>
> | $X \backslash Y$  | 0         | 1         | 4         | Loi de $X$   |
> | :-----:           | :-------: | :-------: | :-------: | :----------: |
> | -2                | 0         | 0         | $\frac16$ | $\frac 16$   |
> | -1                | 0         | $\frac14$ | 0         | $\frac 14$   |
> |  0                | $\frac16$ | 0         | 0         | $\frac 16$   |
> |  1                | 0         | $\frac14$ | 0         | $\frac 14$   |
> |  2                | 0         | 0         | $\frac16$ | $\frac 16$   |
> | Loi de $Y$        | $\frac16$ | $\frac12$ | $\frac13$ | 1            |
>
> **Loi marginale de $Y$**
> D'aprés le tableau de la loi conjointe 
>
> | $X \backslash Y$  | 0         | 1         | 4         | 
> | :-----:           | :-------: | :-------: | :-------: | 
> | $\mathbb P(Y=Y_i)$| $\frac 16$| $\frac 12$| $\frac 13$ | 
>
> **Indépendance**
> $P_{ij} = \mathbb P((X=i) \cap (Y=j)) =^? \mathbb P(X=i) \cdot \mathbb P(Y=j) ~\forall (i,j)$
> Or $P_{ij} = \mathbb P((X=0) \cap (Y=1)) = 0 \neq \mathbb P(X=0) \cdot \mathbb P(Y=1) = \frac16 \cdot \frac12 = \frac{1}{12}$ 
> $\Rightarrow$ $X$ et $Y$ ne sont pas indépendants
>
> **La covariance**
>
> $$Cov(X,Y) = E(X \cdot Y) - E(X)E(Y) \\
E(X \cdot Y) = \sum_{i,j} ij \mathbb P_{i,j} = \sum_{i} i \sum_{j} j \mathbb P_{i,j} \\
> \text{avec } P_{i,j}=\mathbb P((X=i)\cap (Y=j)) \\
E(XY) = -\frac 86 - \frac 14 + \frac 14 + \frac 86 = 0$$
> $$E(Y) = \sum i \mathbb P (Y=i)= \frac 12 + \frac 43 = \frac{11}{6}$$
> $$E(X) = \sum i \mathbb P (X=i)= -\frac 13 - \frac 14 + \frac 14 + \frac 13 = 0$$
> :::success
> $Cov(X, Y) = 0$
> On peut noter que lorsque **X** et **Y** sont indépendante la covariance est nulle. Cependant la réciproque n'est pas vrai.
> La preuve dans cet exercice **X** et **Y** sont dépendante et leur covariance est nulle.
> :::

> **Exercice 2**
> On a $n$ boîtes numérotées de $1$ à $n$
> La boîte n°$k$ contient $k$ boules numérotées de 1 à $k$.
> On choisit au hasard une boîte puis une boule dans cette boîte.
> $X$ V.A le numéro de la boîte
> $Y$ V.A le numéro de la boule
>
> 1) Déterminer la loi conjointe
> 2) Calculer $\mathbb P(X=Y)$
> 3) Déterminer la loi marginale de Y
> 4) Calculer $E(Y)$
>  ---
> $X(\omega) = \{1 ,2 ,\ldots ,n\}$
> $Y(\omega) = \{1 ,2 ,\ldots ,n\}$
> Loi de couple $(X,Y)$ ?
> $\mathbb P((X=i)\cap(Y=j))$
> 
>  $\forall i \in [\![1, n]\!]$
>  $\forall j \in [\![1, n]\!]$
> 
> **Loi conjointe** 
> Soit $j > i$
> $P_{ij} = \mathbb P((X=i) \cap (Y=j)) = 0$
> 
> Soit $j <= i$
> $P_{ij} = \mathbb P((X=i) \cap (Y=j))$
> $= \mathbb P(y=j|X=i) \cdot \mathbb P(X=i)$
> $= \frac{1}{i} \cdot \frac{1}{n}$
> 
> **$\mathbb P(X=Y)$**
> 
> $\mathbb (X=Y) = \displaystyle\bigcup_{i=1}^{n} (X=i) \cap (Y=i)$
> évènements indépendants donc 
> $\mathbb P(X=Y) = \displaystyle\sum_{i=1}^{n} P_{ii} = \displaystyle\sum_{i=1}^{n} \frac{1}{i} \cdot \frac{1}{n} = \frac{1}{n} \cdot \displaystyle\sum_{i=1}^{n} \frac{1}{i}$
>
> **Loi marginal de Y**
> $\mathbb P(Y=j)=\displaystyle\sum_{i}^{n}\mathbb((X=i)\cap (Y=j))$
> $=\displaystyle\sum_{i = j}^{n}\frac{1}{i \cdot n}=\frac{1}{n}\displaystyle\sum_{i = j}^{n}\frac{1}{i}$
>
> **Esperance de Y**
> $E(Y) = \displaystyle\sum_{j=1}^{n} j \cdot \mathbb P(Y=j)$
> $E(Y) = \displaystyle\sum_{j=1}^{n} j \cdot \frac{1}{n} \displaystyle\sum_{i=j}^{n} \frac{1}{i}$
> $E(Y) = \frac{1}{n} \displaystyle\sum_{j=1}^{n} j \displaystyle\sum_{i=j}^{n} \frac{1}{i}$
> $E(Y) = \frac{1}{n} \displaystyle\sum_{i=1}^{n} \frac{1}{i} \displaystyle\sum_{j=1}^{i}j$
> $E(Y) = \frac{1}{n} \displaystyle\sum_{i=1}^{n} \frac{1}{i} \cdot \frac{i(i + 1)}{2}$
> $E(Y) = \frac{1}{2n} \displaystyle\sum_{i=1}^{n} i+1$
> $E(Y) = \frac{1}{2n} (\frac{n(n+1)}{2} + n)$
> $E(Y) = \frac12 (\frac{n+1}{2} + 1)$
> $E(Y) = \frac{n+3}{4}$
> 
> **Exercice**
> On dispose d'un dé équilibré à 6 faces
> et d'une pièce truquée telle que la proba(pile) = $p \in ]0,1[$
> Soit $N \in \mathbb N^{*}$ (fini). On effectue $N$ lancés de dé. Si $n$ est le nombre de six obtenu, on lance alors $n$ fois la pièce.
> $Z$ V.A nombre de six obtenus
> $X$ V.A nombre de pile
> $Y$ V.A nombre de face
> $Z = X + Y$
> $Z = 0$ si $X = Y = 0$
> 
> 1) déterminer la loi de Z, E(Z), V(Z)
> 2) $\forall k \in \mathbb{N}, \forall n \in \mathbb{N}$ determiner $\mathbb P(X=k|Z=n)$
> 3) $\forall 0 \leq k \leq n < N$ calculer $\mathbb P((X=k) \cap (Z=n))$
> 4) calculer $P(X) = 0$
> 5) Montrer que $\forall 0 \leq k \leq n \leq \mathbb{N}$
> 6) En déduire $P(X=k)$  
>    Reconnaître la loi de $X$
> 7) Loi de $Y$ ?
> 8) Calculer $Cov(X, Y)$, $X$ et $Y$ sont-ils indépendants ?
> 9) Loi de $(X, Y)$ ?
> 
> ---
>
> 1) $Z \rightarrow B(N,\frac16)$
> $E(Z) = \frac{N}{6}, V(Z) = N \cdot \frac16 \frac56 = \frac{5N}{36}$
> 
> 2)
> Soit $k > n$ 
> $\mathbb P(X=k|Z=n) = 0$
> Soit $0 \leq k \leq n$
> $\mathbb P(X=k|Z=n) = \binom{n}{k} p^{k} (1-p)^{n-k}$
> 
> Donc $X|Z=n \rightarrow B(n,p)$
> 
> 3) $\mathbb P((X=k) \cap (Z=n)) = \mathbb P(X=k|Z=n) \mathbb P(Z=n)$
> $\forall 0 \leq k \leq n \leq \mathbb{N}$
> $\binom{n}{k} p^k (1-p)^{n-k} \binom{N}{n} (\frac{1}{6})^n(\frac{5}{6})^{N-n}$
>
> 4) ** $P(X=k) = 0$ **
> 
> $\mathbb P(x=0) = \displaystyle\bigcup_{n=0}^{N} (X=0) \cap (Z=n)$
> évènements incompatible donc
> $\mathbb P(x=0) = \displaystyle\sum_{n=0}^{N} P((X=0) \cap (Z=n))$
> $\mathbb P(x=0) = \displaystyle\sum_{n=0}^{N} (n-p)^n \binom{N}{n} \frac16^{n} \frac56^{N-n}$
> $\mathbb P(x=0) = \displaystyle\sum_{n=0}^{N} (n-p)^n \binom{N}{n} \frac{5^{N-n}}{6^N}$
> $\mathbb P(x=0) = \frac{1}{6^N} \displaystyle\sum_{n=0}^{N} \binom{N}{n} (1-p)^n 5^{N-n}$
> $\mathbb P(x=0) = \frac{1}{6^N} (6 - p)^N$
> $\mathbb P(x=0) = (1 - \frac{p}{6})^N$
> 
> Formule de Binôme de Newton
> $(a + b)^N = \displaystyle\sum_{n=0}^{N} \binom{N}{n} a^n b^{N-n}$
> 
> 5) $\binom{n}{k} \binom{N}{n} =? \binom{N}{k} \binom{N-k}{n-k}$
> 
> $\frac{n!}{k!(n-k)!} \frac{N!}{n!(N-n)!} = \frac{N!}{k!(N-k)!} \frac{(N-k)!}{(n-k)!(N-n)!}$
> les deux expressions se simplifient en 
> $\frac{N!}{k!(n-k)!(N-n)!}$
>





## Description multidimensionnelle

### Tableau de données

### Matrice de poids

### Centre de gravité

### Matrice de variance

### Covariance et matrice de corrélation

### Espace des individus et espace des variables

### Methode ACP

:::info
Méthode ACP = Analyse Composante Principale
On a une matrice
$P$ variables (colonnes)
$n$ Individus (lignes) : population de pressions, vitesses, objets, habitants...
Un élément de la matrice $i,j =$ valeur de $P_j$ pour l'individu $i$
:::

:::info
[**Inertie**](http://jybaudot.fr/Stats/inertie.html) : moyenne des distances au carré des points au [**barycentre**](https://fr.wikipedia.org/wiki/Barycentre).
:::

#### Axe factoriels

#### Composantes principales

#### Corrélation linéaire

















