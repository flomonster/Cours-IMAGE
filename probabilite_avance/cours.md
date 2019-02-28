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









