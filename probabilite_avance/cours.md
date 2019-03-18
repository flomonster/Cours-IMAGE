# Probabilités et statistiques (niveau avancé)

:::success
On a le droit à un support pour le partiel !!! :+1: 
:::

:::warning
Ne pas oublier le SAV **Tochon**
![](https://i.ytimg.com/vi/RejSOsIq8iE/hqdefault.jpg)
:::

## Rappels

* $\Omega$ : L'ensemble des expériences que l'on peut faire
* $\omega \in \Omega$ : Une expérience
* $\omega \longrightarrow (X(\omega), Y(\omega))$ : C'est le fait de réaliser  l'expérience (et d'obtenir un résultat, ici une position $x$ et $y$)

---

Formellement :

* $\Omega$ : L'ensemble des événements élémentaires
* $\omega \in \Omega$ : Un événement élémentaire
* $A \subset \Omega$ : Un événement, $A \in \mathcal{P}(\Omega)$ : *"A parti de Omega"*
* Quand $A$ se produit, on dira *"A est vrai"*.
* Quand $A^c$ ou $\bar{A}$ se produit, on dira *"A est faux"*.
* Quand $A \cap B$ se produit, on dira *"A et B"*.
* Quand $A \cup B$ se produit, on dira *"A ou B"*.
* $A \subseteq B$ se dira *"Si A alors B"*.
* $\emptyset$ est *impossible*.
* $\Omega$ est *certain*.

Une tribu $\mathcal{F}$

* $\emptyset \in \mathcal{F}$
* $A_1,\dots,A_n \in \mathcal{F} \Longleftrightarrow \displaystyle \bigcup_{i=1}^\infty \{A_i\}\subseteq \mathcal{F}$
* $A\in \mathcal{F}$ et $A^c \in \mathcal{F}$

$$
A \rightarrow \mathbb{P}(A) \in[0,1]\\
\mathbb{P}(\emptyset) = 0\\
\mathbb{P}(\Omega) = 1\\
A_1 \dots A_n \forall i,j \: i \ne j)\\
A_i \cap A_j = \emptyset\\
P(\bigcup_{i=1}^\infty A_i )= \sum_{i=1}^\infty P(A_i)
$$
$(\Omega, \mathcal{F}, P)$: Espace probabilisé

Une experience:
\begin{matrix}
             &                  & oui& non  \\
    \omega_1 & ? ~ \omega_1 \in A & 1 & 0.R_1 \\
    \omega_2 & ? ~ \omega_2 \in A & 1 & 0.R_2 \\
             & \vdots           &   &       \\
    \omega_n & ? ~ \omega_n \in A & R_n = 1 & R_n = 0 \\
             & \vdots           &   & 
\end{matrix}


$(R_1, ..., R_{50 000 000})$

$\bar{a}n$ je connais $R_{1} \dots R_{n}$
frequence $f_n = \frac{R_1 + \dots + R_n}{n}$

**Propriétés :**
* $\mathcal{P}(A^c)=1-\mathcal{P}(A)$
* $\mathcal{P}(A \cup B)=\mathcal{P}(A) + \mathcal{P}(B) - \mathcal{P}(A \cap B)$

#### Probabilité conditionnelles

* $\mathcal{P}(A | B) = \frac{\mathcal{P}(A \cap B)}{\mathcal{P}(B)}$
* $\mathcal{P}(A) = \mathcal{P}(A | B)\mathcal{P}(B) +\mathcal{P}(A | B^c)\mathcal{P}(B^c)$
* $\mathcal{P}(A \cap B) = \mathcal{P}(A|B)\mathcal{P}(B) = \mathcal{P}(B|A)\mathcal{P}(A)$
    :::success
    **Théorème de Bayes**
    $$\mathcal{P}(A | B) = \frac{\mathcal{P}(B|A)\mathcal{P}(A)}{\mathcal{P}(B)}$$
    :::

### Variable aléatoire

\begin{align}
X: \Omega &\to \mathbb{R}\\
   \omega &\mapsto X(\omega)
\end{align}

---

**Fonction de répartition :**

\begin{align}
F_X: \mathbb{R} &\to [0;1] \\
            x   &\mapsto \mathcal{P}(X \leq x)
\end{align}

$\mathcal{P}(X \in ]a,b]) = F(b) - F(a)$

Si $X$ continu:
* $\mathcal{P}({a})=0$
* $\mathcal{P}(a < X \leq b) = F(b) - F(a)$
* $\mathcal{P}(a < X) = 1 - F(a)$


$A_1 \dots A_n$ événements indépendants de même probabilité $p$

* $\mathbb{I}(A)$: La fonction caractéristique de A
* $\mathbb{I}(A_n)$

$$S_n=\sum_{k=1}^n \mathbb{I}(A_k) ~~~~ f_n=\frac{1}{n}S_n$$

$\forall \epsilon > 0\\
\displaystyle\lim_{n\rightarrow \infty}\mathcal{P}(p-\epsilon \leq f_n \leq p + \epsilon) = 1$


$f(x) :$ densité de probabilité $\mathbb{R} \rightarrow \mathbb{R}^+$
1) A un domaine "Quelconque"

   $\displaystyle\underbrace{\mathbb{R}(X \in A)}_{\mathbb{R}(X(w) \in A)} = \int_A f(x) dx$


2) $\displaystyle \underset{X}{F}(x) = \mathcal{P}(X \leq x) = \int_{-x}^{x} f(t) dt$


### Espérance

$\displaystyle\mathbb{E}(X) = \int_{-\infty}^{+\infty}xf(x)\,dx$


De maniere générale, si on prend nimporte quelle fonction:
$g : \text{ une fonction de } \mathbb{R} \rightarrow \mathbb{R}$
$\displaystyle\mathbb{E}(g(X)) = \int_{-\infty}^{+\infty}g(x)f(x)\,dx$

$X, Y (x,y) \text{ la densite de } f(x,y)$

$\mathbb{E}(g(X,Y)) = \iint g(x,y)f(x,y)\,dx\,dy$

3) $\displaystyle\int^{+\infty}_{-\infty} f(x)dx = \int_{-\infty}^{+\infty}1f(x)dx = 1$

---

Exemple:
> La loi uniforme sur $[0,1] : U$
> Densité constante $d$
> 
> ![Graph de densité](https://upload.wikimedia.org/wikipedia/commons/thumb/9/9c/Uniform_distribution_PDF.png/280px-Uniform_distribution_PDF.png)
> 
> $\displaystyle \int_{-\infty}^{+\infty} f(x)~dx = \int_0^1 f(x)~dx = \int_0^1 d~dx = d$
> $\displaystyle\mathbb{E}(U) = \int_\mathbb{R} xf(x)dx = \int_0^1 xdx = [\frac{x^2}{2}]_0^1 = \frac{1}{2}$


Variable Aléatoire $X$ de densite $d(x)$
* "Moyenne": **Esperance** : $f(x) = \int x f(x) dx$ = $ m(x)$ = $m_x$
* "Ecart quadratique moyen" **Variance** : $Var(x) =\mathbb{E}((X - m_x)^2)$
* **Ecart type** : $\sigma(x) = \sqrt{Var(x)}$

$X,Y$ deux Variables aleatoires
$\alpha, \beta \in \mathbb{R}^2$
$\mathbb{E}(\alpha X + \beta Y) = \alpha \mathbb{E}(X) + \beta\mathbb{E}(Y)$
$\mathbb{E}(X + Y) = \mathbb{E}(X) + \mathbb{E}(Y)$

$X, Y = X!$
$X + Y = 2X!$
$\mathbb{E}(X + Y) = 2m_x$
$Var(X + Y) = \mathbb{E}((X + Y  - 2m_x)^2) = \mathbb{E}((2cx - m_x))^2$
$\sigma(X+Y) = 2\sigma(X) = \sigma(X) + \sigma(Y)$

---

$X,Y = -X$
$X +Y = 0$

$\mathbb(E)(X) = m_x$
$\mathbb{E}(Y) = m_y$

\begin{align}
Var(X + Y) &= \mathbb{E}((X+Y-m_x-m_y)^2)\\
&= \mathbb{E((X + 1)^2) - (m_x + m_y)^2}
\end{align}

\begin{align}
Var(X) &= \mathbb{E}((X-m_x)^2) = \mathbb{E}(X^2 - 2m_xX+m_x^2)\\
&= \mathbb{E}(X^2) - 2m_x\mathbb{E} + m_x^2\\
&= \mathbb{E}(X^2) - m_x^2
\end{align}

$Var(X + Y) = \mathbb{E}(X^2) + \mathbb{E}(Y^2) + 2\mathbb{E}(XY) - (m_x +  m_y)^2$

> X et Y n'ont rien a voir ...

$\mathbb{E}(XY) = \mathbb{E}(X) \mathbb{E}(Y)$
\begin{align}
Var(X+Y) &= \mathbb{E}(X^2) + \mathbb{E}(Y^2)  + 2\mathbb{E}(X)\mathbb{E}(Y) -m_x^2 -m_y^2 -2m_x m_y\\
&= Var(X) + Var(Y)
\end{align}

#### variables aleatiores independantes
$X$ et $Y$ independantes, $\forall x \forall y, \{X \le x\}$ et $\{Y \le y\}$ independants

---

#### Variables aleatoires non correlees.
$\mathbb{E}(XY) = \mathbb{E}(X) \mathbb{E}(Y)$
> Si elles sont *correlees* ? On centre les variables aleatoires

$X^* = X - m_x \:\:\: \mathbb{E}(X^*) = 0$
$Y^* = Y - m_y \:\:\: \mathbb{E}(Y^*) = 0$

$\mathbb{E}(X^* Y^*) = \rho \sigma(X^2)\sigma(Y^2)$
$= \rho \sigma(X) \sigma(Y)$
$\mathbb{E}((X-m_x)(Y-m_y)) =$ **Covariance**

$Cov(X,Y) = \mathbb{E}((X-m_x)(Y-m_y))$
$\rho = \frac{Cov(X,Y)}{\sigma(X)\sigma(Y)}$ "coefficient de correlation" $\in [-1, 1]$

\begin{align}
Var(X + Y) &= Var(X^* + Y^*)\\
&= \mathbb{E}((X^* + Y^*)^2)\\
&= \mathbb{E}((X^{*2}+ 2x^*Y^*)^2)\\
&= \mathbb{E}(X^{*2}) + 2\mathbb{E}(X^*Y^*) + \mathbb{E}(Y^{*2})\\
&= \sigma^2_x + 2\rho_{xy}\sigma_{X^{*}}\sigma_{Y^{*}} + \sigma^2_{X^*}\\
\end{align}

$Var(X + Y)= \sigma_x^2 + 2\rho_{xy}\sigma_x\sigma_y+ \sigma_y^2$
$Var(aX + bY) = \sigma^2_X a^2 + 2\rho_{xy}\sigma_x\sigma_y a b + \sigma_y^2 b^2$


**Cauchy-Schwarz :**
$$\mathbb{E}(XY)^2 \leq \mathbb{E}(X^2)\mathbb{E}(Y^2)$$

**Bienaymé-Tchebychev :**
$$\mathbb{P}(|X-m_X \geq a) \leq \frac{\sigma^2_X}{a^2}$$


### Exercices
#### Exercice 1

Soit X une variable aléatoire de loi exponentielle de paramètre $\lambda$
.Cf. le slide 32.
Avec un logiciel, effectuer une simulation et dessiner un histogramme des valeurs obtenues.
Reconnaissez vous la forme de la densité ?

```python=
import numpy as np
import matplotlib.pyplot as plt

x = np.random.exponential(sclae=1, size=100000)
plt.hist(x, normed=True, bins=100)
plt.show()
```

![](https://i.imgur.com/xAXqueB.png)


#### Exercice 2

Soient X et Y deux variables aléatoires dont la loi conjointe est donnée par la densité f suivante :

$$f(x,y) \begin{cases}  &2 e^{-x -y} &\text{ si } 0< x < y\\ &0 &\text{ sinon }\end{cases}$$

1. Si vous disposez d'un outil de représentation 3D, essayez de donner une
représentation graphique de la densité f.
2. Vérifiez que f est bien une fonction de densité.
3. Calculer les lois marginales de X et Y et reconnaître autant que possible la nature de X et Y.
4. Calculer les densités des lois conditionnelles $f_{X,Y=y}$ et $f_{Y,X=x}$. Quand c’est possible, reconnaître la nature de ces nouvelles variables aléatoires.
5. Calculer les espérances $\mathbb E(X)$ et $\mathbb E(Y)$.
6. Calculer les espérances conditionnelles $\mathbb E(X|Y)$ et $\mathbb E(Y|X)$.
7. Calculer la covariance de X et Y
8. Calculer le coefficient de corrélation de X et Y. Interpréter le résultat.


#### 1) 
![](https://i.imgur.com/ZpZKJj8.png)



#### 2) 
$$\begin{align} 
& \displaystyle\int_{x\in \mathbb R}\int_{y \in \mathbb R} f(x,y) ~dx dy \\
=& \iint_{0<x<y} f(x,y) dx dy \equiv \int_{x = 0}^{\infty}\int_{y = x}^{\infty} f(x,y) dx dy\\
=& \int^{\infty}_{x=0}\Big\{\int_{y=x}^{\infty}f(x,y) dy\Big\}dx \\
=& \int^{\infty}_{x=0} dx \Big(\int_{y=x}^{\infty} 2e^{-x-y} dy\Big) \\
=& \int^{\infty}_{x=0} 2 e^{-x}dx \Big(\int_{y=x}^{\infty} 2e^{-y} dy\Big) \\
=& \int^{\infty}_{x=0} 2 e^{-x} \Big[-e^{-y} \Big]_x^{\infty} dx\\
=& 2\int^{\infty}_{x=0} e^{-x} e^{-x} dx = 2 \int_0^{\infty} e^{-2x}dx\\
=& \frac 22 [e^{-2x}]_0^{\infty }=1
\end{align}$$

#### 3)

| X                | Y                | 
| :--------------: | :--------------: | 
|                  |                  |


\begin{align}
\begin{cases} f(x,y) &= 2 e^{-(x+y)} \qquad x <y \\
&= 2e^{-s} \qquad \text{où s = (x + y)}\end{cases}
&= \int_x^\infty 2 e^{- x -y} dy\\
&= 2e^{-x} \int_x^\infty e^{-y} dy\\
f(x) = 2e^{-2x}&\\

#### 5) 

\text{Loi exponentienne }\lambda = 2
\end{align}

\begin{align}
f_Y(y) &= \int^{\infty}_{x = 0} f(x,y) dx\\
&= \int^y_{x = 0}2e^{-x-y}dx
\end{align}

\begin{align}
X \text{Exponentiel,} \lambda = 2\\
\mathbb E (X) &= \frac{1}{2}\\
\mathbb{E}(X) &= \int_0^\infty f_x (x) dx\\
&= \iint_{0<x<y} x f(x,y) dxdy\\
\mathbb E(Y) &= \int_0^{\infty} y f_y(y) dx \\
&= \int_0^{\infty} y (2 e^{-y}(1 - e^{-y}))dy\\
&= \int_0^{\infty} (2ye^{-y} - 2ye^{-2y})dy\\
\end{align}


\begin{align}
2\int_{0}^{\infty} y e^{-y} dy - \int_0^{\infty} (2y)e^{-2y} dy\\
= 2 \mathbb{E}(Exp(\lambda = 1)) - \mathbb{E}(Exp(\lambda = 2))\\
=1 - \frac{1}{2} = \frac{3}{2}\\
\text{Loi marginale pour X:}\\
f_x(a) = \int_{y \in \mathbb R} f(x,y) dy \\
\end{align}

:::info
Densite Marginale de X:
Projeté des autres dimensions sur x, tel que x devient l'abcisse de la projection
:::

#### 4) Loi conditionnelle:
$f(x,\underline{\underline{y}})$

$d_{Y|X =x} = \frac{f(x,y)}{\int_y f(x,y)}$

$\frac{f(x,y)}{f_x}(x)$

la Loi conditionnelle de Y connaissant X : $= 0$ si $y \le x$ 
$f_{Y|X =x} = \frac{f(x,y)}{f_X(x)}$
$= \frac{2e^{-x-y}}{2e{-2x}}$
$= e^{x-y} = e^{-(y-x)}$

Loi conditionnelle de X connaissant Y:

$f_{X|Y =y} = \frac{f(x,y)}{f_Y(y)} = 0$ si $x \le 0$ ou $x \ge y$
si $0 < x < y$
$f_{X|Y = y} = \frac{2e^{-x-y}}{2e^{-y}(1 -e^{-y})} = \frac{1}{1  - e^{-y}} e^{-x}$

#### 6) Esperance conditionnelle
$X = x$
$f_{Y|X =x}$
$(y) = \begin{cases}0 \text{si} y \le x \\ e^{-(y - x)} \text{si} y > x\end{cases}$

$Y - x \equiv Exp(1)$

E(Y - x) = 1
$E(Y | X=x) = x + 1$

:::success
\begin{align}
E(Y | X) = X + 1
\end{align}
:::
$\mathbb E(X | Y=y) = \int x f_{x|Y=y}(x) dx$
:::success
\begin{align}
\mathbb E(X | Y=y) = 1 - \frac{ye^{-y}}{1-e^{-y}}
\end{align}
:::

#### 7)

\begin{align}
Var(X) &= \sigma^2(X)\\
&= \mathbb E((X- \mathbb E(X))^2)\\
&= \mathbb(X^2) - (\mathbb E(X))^2
\end{align}

\begin{align}
Var(X) &= \iint_{0<x<y} x^2f(x,y)dxdy\\\
&= 2\iint_{0<x<y}x^2e^{-x-y}dxdy\\
\end{align}

Plus simplement, X suit la loix exponentielle avec $\lambda = 2$
Donc $\sigma(X) = \mathbb E(X) = \frac 1 2$ donc $Var(X) = \frac 1 4$


$\mathbb E (Y^2) = \iint_{0<x<y} y^2 f(x,y) dxdy$
$= \int_{y = 0}^{\infty} y^2 f_y(y) dy$
$= 2\int_0^\infty y^2 e^{-y}(1 - e^{-y}) dy$
$Var(y) = \mathbb E(Y^2) - \mathbb E(y)^2 = \frac 7 2 - \frac 9 4$
$\sigma(y) = \frac{\sqrt 5}{2} = \frac \sigma 4$




--- 
### Theoremes
1) Theoreme de la limite centrale 
https://fr.wikipedia.org/wiki/Th%C3%A9or%C3%A8me_central_limite

2) loi dite "gentille" 

Soit $X$ une loi normale $\mathcal{N}(\mu, \sigma^2)$, on a:

- $\mathbb{P}(|X-\mu| \leq 2\sigma) \approx 95,45\%$
- $\mathbb{P}(|X-\mu| \leq 3\sigma) \approx 99\%$
- $\mathbb{P}(|X-\mu| \leq 6\sigma) \approx (1 - 10^{-9})\%$





La fonction de densité $\varphi$ de la loi normale $\mathcal N(\mu, \sigma^2)$ est définie par :

$$
\varphi_{\mu,\sigma}(x) = \frac{1}{\sigma\sqrt{2\pi}} e^{-\frac{1}{2}\left(\frac{(x - \mu)^2}{\sigma^2}\right)}
$$

Z ~ N(0,1)
X ~ mu + sigma * Z

a,b :
Y = a + bZ
Y ~ N(a, b^2)
W  = a + bX
W ~ N(a + b*mu, (|b|r)^2)
$\mathbb E(W) = \mathbb E(a+bX)$
$a+ \mathbb E(B) = a + b * \mathbb E(X)$

N(0,1) la loi normale standard
$\phi(x) = \frac{1}{\sqrt{2x}} e^{\frac{-1}{2} x^2}$

fonction de répartition $\Phi(x) = \int_\infty^x\phi(t) dt$


En général:
X : f(x)
Y : g(x)
X, Y independants
X + Y = Z densité h

ceci est un produit de convolution:
$h(Z) = \int_{t=-\infty}^{ t=\infty}(f(t)g(Z-t) dt)$

#### Admis

$$
X_1 \sim \mathcal N (\mu_1, \sigma_1^2)\\
X_2 \sim \mathcal N (\mu_2, \sigma_2^2)\\
X_1 + X_2 \text{ : independants}\\ 
X_1 + X_2 \sim \mathcal N(\mu_1 + \mu_2; \sigma_1^2 + \sigma_2^2)
$$

#### Theoreme de la limite centrale

Soient $X_1,..., X_n....$ de Variables Aleat. independantes et identiquement distribuees. esperance $\mu$ et ecart type $\sigma$
$S_n = X_1 + ... + X_n$
* convergenace de la fonction de repartition
$$
\frac{S_n - n\nu}{\sigma\sqrt{n}} \underbrace{\rightarrow}_{\text{loi}} \mathcal N (0,1)
$$

## Statistique Multidimensionnelle

* Vecteur aleatoire
    * $X = \begin{pmatrix} x_1 \\ . \\. \\.\\ x_n \end{pmatrix}$
* Densité
    * $f(x_1, ... , x_n)$

* $\mathbb E(X)$ (moyenne)
    * $\mathbb E(X) = \begin{pmatrix}  \mathbb E(X_1) \\.\\.\\.\\ \mathbb E(X_n) \end{pmatrix}$

* Variance
    * $\sigma_1^2 = \mathbb E ((X_1  - \mathbb E(X_1))^2)$
    * $\sigma_2^2 = \mathbb E ((X_2  - \mathbb E(X_2))^2)$

* Covariance
    * \begin{align}Cov(X_1, X_2) &= \mathbb E((X_1 - \mathbb E(X_1)).(x_2-\mathbb E(X_2))) \\
    &= \underbrace{\rho{12}}_{\text{valeur de correlation }\in[-1,1]} . \sigma_1 . \sigma_2\end{align}
    
* Matrice de Covariance

\begin{align}
\Sigma = \begin{pmatrix} \sigma_1^2 & \sigma_{12} = \rho_{12} \sigma_1 \sigma_2 \\
\rho_{12} \sigma_1 \sigma_2 & \sigma_2^2\\
\end{pmatrix}\\
\Sigma = \begin{pmatrix}
Cov(X_i,X_j)_{1 \le i \le n \text{ et } 1 \le j \le n}
\end{pmatrix}\\
\Sigma &= \begin{pmatrix}
\Sigma_{ij}\\
\end{pmatrix}\\
\Sigma &= \begin{pmatrix}
\Sigma_{11} & \ldots &\ldots & \Sigma_{n1}\\ 
\vdots & \ddots &. & \vdots\\ 
\vdots & . &\ddots & \vdots\\ 
\Sigma_{1n} & \ldots &\ldots & \Sigma_{nn}\\ 
\end{pmatrix}
\end{align}
    
    
## Loi normale multidimentionnelle multivariée

(Cas le plus courrant)

D'espérence $\mu$, de matrice de $var$ / $cov$ $\Sigma$
 
de Densite f :
\begin{align}
f(x) = \frac 1 {(2 \pi)^{\frac n 2}det(\Sigma)^\frac 1 2} * e^{-\frac 1 2 (x -\mu)^t \Sigma^{-1}(x - \mu)}
\end{align}

### Proprietes de matrice de Variance/Covariance

1) $X \mu \Sigma$ en dimension $n$
$X = \begin{pmatrix} X_1\\ \vdots \\ X_n \end{pmatrix}$
$a = \begin{pmatrix} a_1\\ \vdots \\ a_n \end{pmatrix}$
$Y = a_1X_1 + ... + a_n X_n ; a_i \in \mathbb R$
$= a^t . X$

$\mathbb E(Y) = \Sigma a_i \mu_i = a^t \mu$
$Var(Y) = Var(a^tX)$
$= cov(\sum a_i X_i, \sum a_j X_j)$
$= \sum_{i,j} a_i a_j cov(X_i X_j)$

\begin{align}
cov(X,X) &= \mathbb E ((x - \mathbb E(X))(x - \mathbb E(X)))\\
&= cov(aX + bY, Z)\\
&= \mathbb E(\mathbb E([aX +bY - \mathbb E (aX + bY)],[Z - \mathbb E(z)]))\\
&= a cov(X,Z) + b cov(X,Z)\\
&= a^t \sum a
\end{align}

2) Cette formule se generalise

$X$ vecteur aleatoire, $\mu \sigma$
$A$ une matrice
$Y = A.X$
$E(Y) = A.\mu$
:::info
(simple produit matriciel)
$\Sigma_y = A\Sigma A^t$
:::

3) On admet

$B: B^{-1} = B^t$
$B B^t = Id$
$\exists B$
$\exists \Lambda$ diagonale
$\Sigma = B\Lambda B^t$

$X$ un vecteur quelconque
$\mu$
$\Sigma$
$\Sigma = B\Lambda B^t$
On pose $Y = B^tX$
$\Sigma_y = B^t \Sigma_x B$
$= B^t B \Lambda B^tB$
$\Sigma_y = \Lambda$

:::info
Soit $\mu_i = E(X_i)$
Soit $X_i$ la loi suivant $\mathcal N(\mu_i,\sigma_i^2)$
Soit $\Sigma_{\text{dim3}} = \begin{pmatrix}
\sigma_1^2 & \rho_{12} \sigma_1 \sigma_2 & \rho_{13} \sigma_1 \sigma_3\\
 \rho_{21} \sigma_2 \sigma_1 & \sigma_2^2 &\rho_{23} \sigma_2 \sigma_3\\
 \rho_{31} \sigma_3 \sigma_1&\rho_{23} \sigma_3 \sigma_2 & \sigma_3^2 \\
\end{pmatrix}$
On admet un matrice $B$ calculee grace a l'ordinateur.
Soit $\Sigma_x = B \Sigma_y B^{-1}$
Donc $\Sigma_y = B^{-1} \Sigma_x B$
Soit $X = BY$
Donc $Y = B^tX$
En gros: on a un vecteur $X(X_1, X_2, X_3)$ de variables correles, on change de repere en digonalisant la matrice de covariance $\Sigma_{\text{x}}$ de $X$, pour les decoreller, on obtient les valeurs de $B$, on en deduit $B^{-1}$.( C'est une rotation de repere.) On obtient $Y(Y_1, Y_2, Y_3)$, ces variables $Y_i$ sont non correlees.
Ca fait apparaitre des parametres plus interessants, car decorreles.
:::








