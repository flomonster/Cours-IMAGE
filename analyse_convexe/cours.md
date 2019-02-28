---
title: "ACPM"
date: "20-2-2019"
link: "https://hackmd.io/_VubzVxiQP2u-x8S7qEUAQ?both"
tags: SCIA, IMAGE, cours
---

[Bashar's Github](https://github.com/bashardudin/Epita-SCIA-OCVX)


:::info
bashar.dudin@epita.fr
guillaume.tochon@lrde.epita.fr
:::

À voir :
* [Descente de gradient](https://www.youtube.com/watch?v=IHZwWFHWa-w)

# Analyse convexe et programmation mathématique

## Introduction

En rentrant dans l'ère industrielle, il a fallu optimiser les coûts, minimiser les risques, etc.
Des mathematiciens ont commencé à se poser des questions.
ex: gestion d'un stock, optimiser la construction de produits en usine.

* Algebre linéaire
* Calcul différentielle
* Géometrie

> Examples:
> 1. Chercher le plus cours chemnin entre deux coordonnées GPS.
> 2. Décider des meilleurs routes aériennes qui minimisment le prix d'approvisionnement en kérosène.
> 3. Identifier des images d'IRM qui correspondent à des malformations du cerveau.
> 4. Chercher des patterns dans la population d'étudiants intégrants EPITA.

### Problèmes d'optimisation

#### Définition formelle

Minimiser $f_0(x)$
sujet à :
* $f_i(x) \leq 0, \forall i \in \{1,\dots,p\}$
* $h_j(x) \leq 0, \forall j \in \{1,\dots,m\}$

où $f_0$, les $f_i$ et les $h_i$ sont des applications de $\mathbb{R}^n$ vers $\mathbb{R}$. La fonction $f_0$ est dite **fonction objetif**; suivant le contexte ce sera une fonction de **coût** ou d'**erreur**.

Un proble d'optimisatio du type de $(P)$ :
* **différentiable** si toute les fonctions en jeu le sont.
* **non-contraint** s'il n'a aucune contraintes d'inégalités ou d'égalités.
* **convexe** si l'ensemble des fonctions en jeu sont convexes, les contraintes d'égalités étant de plus affines.

#### Lexique

Étant donnée un problème d'optimisation $(P)$ on appelle:
* **point admissible** de $(P)$ tout point de $\mathbb{R}^n$ satisfaisant toutes les contraintes. L'ensemble de tous les points admissibles est appelé **lieu admissible** de $(P)$.
* **valeur objectif** d'un point admissible la valeur que prend la fonction objectif en celui-ci.
* **valeur optimale** de $(P)$ la meilleure borne inférieure sur la fonction objectif.
* **point optimale** de $(P)$ tout point admissible dont la valeur objectif est la valeur optimale.

#### Premières remarques qualitatives

* Y a-t-il au moins une solution ?
* S'il y a au moins une soluton, combien ?
* Peut-on toujours décrire l'ensemble des solutions?
* Y a-t-il moyen d'approcher des solutions?

### ML

#### Map fitting

Problème d'optimisation dit de *map fitting*

:::success
**Définition :**
Une famille différentiable d'applications $f_\alpha:\mathbb{R}^n\longmapsto\mathbb{R}$ indéxeś par $\alpha \in \mathbb{R}^k$ est une famille de fonctions pour laquelle l'application $\phi:\mathbb{R}^k\times\mathbb{R}^n\longmapsto\mathbb{R}$ qui envoie $(\alpha,x)$ sur $f_\alpha(x)$ est différentiable.
:::

:::info
**Map Fitting :**
On considère une ensemble de couples $(X_i, y_i)\in\mathbb{R}^n\times\mathbb{R}$ pour $i \in \{ 1,...,p \}$ et une famille differentiable d'applications $\{ f_\alpha \}_{\alpha\in\mathbb{R}^k}$. Le problème de *map fitting* relatif aux données précédentes consiste à trouver les meilleurs paramètres $\alpha^*$ tels que $f_{\alpha^*}$ approche au mieux les $(X_i, y_i)$. 
:::

#### Régression linéaire

Le plus simple des problèmes de *map fitting* est celui de la régression linéaire.

* La famille différentiable à laquelle on s'intéresse est indexés par $\mathbb{R}^2$: $f_\alpha(x)=\alpha_1x+\alpha_0$ pour $\alpha=(\alpha_0,\alpha_1)$
* La métrique standard utilisée est le **MSE** (Mean Square Error) donnée pour un $f_\alpha$ par
$$\mathcal{E}(\alpha)=\sum_{i=1}^p\frac{1}{p}(f_\alpha (X_j)-y_i)^2$$

Le but est de trouver un paramètre $\alpha = (\alpha_0,\alpha_1)$ tel que $\mathscr{E}(\alpha)$ est minimal, autrement dit de réoudre le problème d'optimisation sans contraintes

### Contour du cours

* La première partie est noté par un TD et un partiel
* La seconde partie est noté par une analyse à faire (projet?)

## Classification

> Comment séparer la classe1 de la classe2 ?
> 
> ![Classification Schéma](https://www.researchgate.net/profile/Ammar_Chouchane/publication/303899174/figure/fig18/AS:614128192323590@1523430979027/Classification-SVM-a-SVM-lineaire-separation-par-une-ligne-droite-b-SVM-non.png)
>
> On fait un trait...


### Produit scalaire

$x = \begin{pmatrix}x_1 \\ \vdots \\ x_n\end{pmatrix} \qquad y = \begin{pmatrix}y_1 \\ \vdots \\ y_n\end{pmatrix}$

$\begin{align}
\langle:\rangle : ~ & \mathbb{R}^n\longmapsto \mathbb{R}\\
                 & (x,y) \longmapsto \langle x,y \rangle
\end{align}$

$\langle x,y \rangle =\displaystyle\sum_{i=1}^{n}x_iy_i$

$||x|| =\sqrt{\langle x,x \rangle}$

On veut :
* $x_1, x_2$ en fonction de $||x||$ et $\phi$
* $y_1, y_2$ en fonction de $||y||$ et $\psi$


* $x_1 = ||x|| \cos{\phi} \qquad x_2 = ||x|| \sin{\phi}$
* $y_1 = ||y|| \cos{\psi} \qquad y_2 = ||y|| \sin{\psi}$

* $\langle \vec{x}, \vec{y}\rangle = x_1 y_1 + x_2 y_2 = ||x||.||y||.(\underbrace{\cos{\phi}\cos{\psi} + \sin{\phi}\sin{\psi}}_{\cos{(\psi - \phi)} = \cos{\theta}}) =||x||.||y||.\cos{\theta}$ 

:::info
**En dimension n :**
$$\theta(x,y)=arccos\left(\frac{\langle x,y \rangle}{||x||.||y||}\right)$$
:::

:::info
**Formules usuelles trigonometriques :**
\begin{align}
\sin \left(s+t\right)=\sin \left(s\right)\cos \left(t\right)+\cos \left(s\right)\sin \left(t\right)\\
\sin \left(s-t\right)=\sin \left(s\right)\cos \left(t\right)-\cos \left(s\right)\sin \left(t\right)\\
\cos \left(s+t\right)=\cos \left(s\right)\cos \left(t\right)-\sin \left(s\right)\sin \left(t\right)\\
\cos \left(s-t\right)=\cos \left(s\right)\cos \left(t\right)+\sin \left(s\right)\sin \left(t\right)\\
\cos \left(s\right)\cos \left(t\right)=\frac{\cos \left(s-t\right)+\cos \left(s+t\right)}{2}\\
\sin \left(s\right)\sin \left(t\right)=\frac{\cos \left(s-t\right)-\cos \left(s+t\right)}{2}\\
\sin \left(s\right)\cos \left(t\right)=\frac{\sin \left(s+t\right)+\sin \left(s-t\right)}{2}\\
\cos \left(s\right)\sin \left(t\right)=\frac{\sin \left(s+t\right)-\sin \left(s-t\right)}{2}\\
\end{align}
:::

On peut représenter une droite avec :
* 2 points
* 1 point et un vecteur directeur ou normal.

$x=\begin{pmatrix} x_1 \\ x_2 \end{pmatrix} \in D \Leftrightarrow \langle \vec{Ox},\vec{n} \rangle = 0 \Leftrightarrow \underbrace{x^{T}n=0}_{\langle x,n \rangle}$
$\rightarrow$ Equation d'un hyperplan de vecteur normal $\vec{n}$

Soit une droite $ax_1 +bx_2 + c = 0$ :
* Son **vecteur normal** : $\vec{n} = \begin{pmatrix}a\\b\end{pmatrix}$
* Son **vecteur directeur** : $\vec{u} = \begin{pmatrix}-b\\a\end{pmatrix}$


> **Exercice :**
> Dessiner le lieu de $\mathbb{R}^2$ donné par la relation
> $$\begin{pmatrix}
> 1 & 2 \\
> -1 & 1
> \end{pmatrix}
> \begin{pmatrix}
>  x_1\\x_2
> \end{pmatrix} \leq \begin{pmatrix}0\\0\end{pmatrix}$$
>
> $x_1 + 2x_2 \leq 0$
> $-x_1 + x_2 \leq 0$
> 
> On remplace l'inégalité par une égalité :
> $x_1 + 2x_2 = 0 \qquad \vec{n_1} = \begin{pmatrix}1\\2\end{pmatrix} \qquad \vec{u_1} = \begin{pmatrix}-2\\1\end{pmatrix}$
> $-x_1 + x_2 = 0 \qquad \vec{n_2} = \begin{pmatrix}-1\\1\end{pmatrix} \qquad \vec{u_2} = \begin{pmatrix}-1\\-1\end{pmatrix}$
>
> On a les vecteurs normaux on peut donc représenter graphiquement le lieu.
> ![](https://i.imgur.com/M8Y0xkz.png)


> **Exercice :**
> Trouver le lieu de $\mathbb{R}^3$ tq $\underbrace{x_1 + x_2 + x_3}_{(1 1 1)\begin{pmatrix}x1\\x_2\\x_3\end{pmatrix}} \geq 0$
> 
> $\vec{n} = \begin{pmatrix}1\\1\\1\end{pmatrix}$
> $\langle n, x \rangle \geq 0$
>
> ![](https://i.imgur.com/kcXCXJE.png)


### Espace affine

$A = {(1,t) \in \mathbb{R}^2 | t \in \mathbb{R}} = (1, 0) + \underbrace{\{(0,t) \in \mathbb{R}^2 | t \in \mathbb{R}\}}_{F}$

:::info
On note qu'on pouvait utiliser un autre point $(1,42)$ au lieu de $(1,0)$ donne le même résultat.
:::


$P=\{(t, 3t + u, -u) \setminus (t, u) \in \mathbb{R}^2\}$
* $O \in P$
* $A = \begin{pmatrix}1\\3\\0\end{pmatrix} \in P$
* $B = \begin{pmatrix}0\\1\\-1\end{pmatrix} \in P$
$\vec{n} = \vec{OA} \times \vec{OB}$

:::info
**Produit vectoriel :** [Wikipédia](https://fr.wikiversity.org/wiki/Produit_vectoriel/Avanc%C3%A9)
:::

> **Exercice :**
> Ecrire **paramétriquement** la droite $D$ de $\mathbb{R}^2$ de vecteur directeur $\vec{u}=\begin{pmatrix}1\\-1\end{pmatrix}$ et passant par $(2,3)$
>
> Soit $M \in D \Leftrightarrow \exists ~\alpha \in \mathbb{R}$ tq 
> $$\vec{AM} = \alpha \vec{u} \\ 
> \Leftrightarrow \begin{pmatrix}x_1 - 2\\ x_2 - 3\end{pmatrix} = \alpha \begin{pmatrix}1\\-1\end{pmatrix}\\
> \Leftrightarrow \begin{cases} x_1 -2 = \alpha \\ x_2 - 3 = -\alpha\end{cases} \\
> \Leftrightarrow \begin{cases}x_1 = \alpha + 2\\x_2 = 3 - \alpha\end{cases}$$
>
> Donc $(D) = \{(\alpha +2, 3-\alpha) | \alpha \in \mathbb{R}\}$

> **Exercice :**
> Dessiner le lien de $\mathbb{R}^2$ decrit par les contraintes :
> $\begin{pmatrix}-1 & 2 \\
> 1 & 1\\ 
> \end{pmatrix} = \begin{pmatrix}x \\ y  \end{pmatrix} \le \begin{pmatrix} -1 \\ 1\end{pmatrix}$
> $ax + by = 0$
> $ax + by +c = 0$
> $\overrightarrow{n} \begin{pmatrix}a \\ b  \end{pmatrix} \overrightarrow{u} \begin{pmatrix}-b \\ a  \end{pmatrix}$
> $\{ (x,y) \in \mathbb{R}^2 , -x + 2y \le -1 \text{ et } x+y \le 1 \}$
> $(D_1) = -x + 2y + 1 = 0$
> $(0, \frac{-1}{2} \in D_1)$
> $\overrightarrow{n_1} = \begin{pmatrix} -1 \\ 2\end{pmatrix}$
> $\overrightarrow{u_1} = \begin{pmatrix} -2 \\ -1\end{pmatrix}$

---

$\underbrace{Ax = r}_{\text{écriture implicite}} \qquad \text{ avec } \begin{cases}\text{A matrice } m \times n\\A = [a_{i,j}]_{mn}\\x \in \mathbb R^n ~ r \in \mathbb R^m \end{cases}$
\begin{cases}
a_{11} x_1 + a_{12} x_2 + \dots + a_{1n}xn = r_1\\
\vdots \\
a_{m1}x_1 + a_{m2}x_2 + \dots + a_{mn}x_n = r_m
\end{cases}

:::info
**Hyperplan**: Un plan de dimension $n-1$.
Exemples: En 2D, c'est une droite. En 3D, c'est un plan...
:::

Notre description affine ne suffit pas dans le cas général.

:::info
**Description d'un cercle :**
$x^2 + y^2 = r^2\\
x^2+y^2-r^2=0$
$\boxed{f(x,y) = x^2 + y^2 - r^2}$
:::

:::info
**Ligne / Courbe de niveau d'une fonction f:**
$$\mathscr{C}_r=\{x\in \mathbb{R}^n | f(x)=r\}$$

**Lieu de sous niveau e d'une fonction f:**
$$\mathscr{C}_{\leqslant r}=\{ x\ \in \mathbb{R}^n \ f(x) \leqslant r \}$$
:::

:::info
Les **coniques :** C'est les paraboles, hyperboles, elipse...
:::

> **Exercice :**
> Courbes de niveau 0,1,2
> 1. $f(x,y)=x^2+y^2$
    > $\mathscr{C}_0$: seul $(0,0)$
    > $\mathscr{C}_1$: cercle de rayon 1 centré en 0
    > $\mathscr{C}_2$: cercle de rayon 2 centré en 0
    > 2. $g(x,y)=x^2+4y^2$
    > $\mathscr{C}_0$: seul $(0,0)$    
    > $\mathscr{C}_1$: ellipse demigrand axe 1, demipetit axe $\frac{1}{2}$, centré en 0
    > $\mathscr{C}_2$: ellipse demigrand axe $\sqrt{2}$, demipetit axe $\frac{\sqrt{2}}{2}$, centré en 0
>
> ![schema cercle](https://i.imgur.com/pJCjNKt.gif)

:::info
**Équation d'une éllipse**
$$\bigg(\frac xa\bigg)^2 + \bigg(\frac yb\bigg)^2=1$$
![](https://i.imgur.com/4I9Oq2K.gif)
**a :** demi-grand axe
**b :** demi-petit axe
:::

:::info
Epigraphe d'une fonction $f.\mathbb R^n \rightarrow \mathbb R$

$Epi(f) = \{(x,t) ~|~ f(x) \leq t\}$

![Représentation épigraphe](https://i.stack.imgur.com/y98sx.png)
:::

> **Exercice :**
> Dessiner l'intersection de l'épigraphe de $f(x)=-\sqrt{x}$ (sur $\mathbb R^+$)
> avec la partie $\{(x, y) | y \leq \sqrt x\}$
> ![](https://i.imgur.com/0R5DgRj.png)

:::success
Une partie de $A\subset \mathbb{R}^n$ est **convexe** ssi $\forall x,y\in A, \forall t\in [0,1]$ alors $$tx+(1-t)y \in A$$
:::

:::info
**L'adhérence** d'une partie est sa frontiere.
$A \cup \partial{A}  = \underbrace{\bar{A}}_{adhérence}$
:::

> **Exemple :**
> $A = [1,2[$
> $\partial A = \{\{1\} \{2\}\}$
> $\bar A = [1,2]$


> Quoi ? Hyper parapluie ??? [name=multun]

:::info
Un **hyperplan d'appui** d'une partie $A$ est un hyperplan de $A$ qui posséde un élément du bord de $A$
![Schema hyperplan d'appui](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcSLLg3Yp48CLVcKGuwVXIXZ8GxKMd8DJ58WHYSagPY4qjq5SX9Sag)
:::

:::info
Une **fonction convexe** admet des hyperplans d'appui en chacun des points de sa frontière.
:::

:::info
$f$ **convexe** $\Leftrightarrow f(tx+(1-t)y) \leq tf(x)+ (1-t)f(y)$
:::


Exemple de fonctions convexes
* $f(x) = ax^2 +bx +c , a \ge 0$
* $f(x) = bx+ c$
* $e^{ax} \quad \forall a$
* $f(x) = -\log(x)$
* $f(x) = \sqrt(x)$
* $f(x) = |x|$
* $f(x) = x^{2p}, p \in \mathbb{N}^*$

> **Exercice :**
> Est ce que la somme de fonctions convexes est convexe ?
> 
> $f = \sum_{i=1}^{N}w_if_i$ la somme de fonctions convexes
>
> $$\begin{align}
> f(tx + (1-tg)) &= \sum_{i=1}^N f_i (tx+(1-t)y) \\
>                &\leq tf_i(x)+(1-t)f_i(y) \\
>                &\leq \sum_{i=1}^N w_i(tf_i(x)+(1-t)f_i(y)) \\
>                &\leq \sum_{i=1}^N tw_if_i(x) + \sum_{i=1}^N(1-t)w_if_i(y) \\
>                &\leq t\underbrace{\sum_{i=1}^N w_if_i(x)}_{f(x)} + (1-t) \underbrace{\sum_{i=1}^N w_if_i(y)}_{f(y)}
> \end{align}$$
> Donc c'est bien convexe !


Soit $f(x,y) = x^2 + y^2$
La fonction [Hessienne](https://fr.wikipedia.org/wiki/Matrice_hessienne) de $f$:
$$H(x,y) = \begin{pmatrix}\frac{\partial^2f(x,y)}{\partial x^2}
&\frac{\partial^2f(x,y)}{\partial y \, \partial x} \\ 
\frac{\partial^2f(x,y)}{\partial y \, \partial x}
& \frac{\partial^2f(x,y)}{\partial y^2}
\end{pmatrix} $$


## Programme linéaire

> **Exercice 1:**
> 
> $\mathcal A_u : \begin{cases}
> -x+2y \leq 1\\
> x + y \leq 1
> \end{cases}$
> 
> $\mathcal A_b = \mathcal A_u \cup \{(x,y) \in \mathbb R^2, x-3y \leq 6\}$
> 
> * $(D_1)$: $-x + 2y + 1 = 0 \qquad (0, -\frac 12) \in (D_1) \qquad \vec{n_1}\begin{pmatrix}-1\\2\end{pmatrix} \qquad \vec{u_1}\begin{pmatrix}-2\\-1\end{pmatrix}$
> 
> * $(D_2)$: $x + y  - 1 = 0 \qquad (0,1) \in (D_2) \qquad \overrightarrow{n_2}\begin{pmatrix} 1 \\ 1\end{pmatrix}\qquad \overrightarrow{u_2}\begin{pmatrix} -1 \\ 1\end{pmatrix}$
> 
> * $(D_3)$: $x - 3y  - 6 = 0 \qquad (0,-2) \in (D_3) \qquad \overrightarrow{n_3}\begin{pmatrix} 1 \\ -3\end{pmatrix}\qquad \overrightarrow{u_3}\begin{pmatrix} 3 \\ 1\end{pmatrix}$
> 
> $\underbrace{\min f_0(x,y) = y = -\infty}_{(x,y) \in \mathcal{A}_u}$
> $\underbrace{\min f_0(x,y) = -y = 0}_{(x,y) \in \mathcal{A}_u}$


> **Exercice 2:**
>
> $f(x,y) = 3x^2 + y^2$
> $\mathcal{C}_2(f)\mathcal{C}_4(f)$?
> $\mathcal{C}_{\le 4}(f)$?
> $\min f_0(x,y) = 2x + y$
> sujet à $3x^2 +y^2 \le 4$
> 
> \begin{align}
> \mathcal{C}_2(f) : &  3x^2 + y^2 = 2 \\
> \Leftrightarrow &\frac{3}{2}x^2 \frac{1}{2}y^2  = 1\\
> \Leftrightarrow &\begin{pmatrix}\frac{x}{\frac{\sqrt{2}}{\sqrt{3}}}\end{pmatrix}^2 + \begin{pmatrix}\frac{y}{\sqrt{2}}\end{pmatrix}^2\\
> \end{align}
> 
> \begin{align}
> \mathcal{C}_4(f) : &  3x^2 + y^2 = 4 \\
> \Leftrightarrow &\frac{3}{4}x^2 \frac{1}{4}y^2  = 1\\
> \Leftrightarrow &\begin{pmatrix}\frac{x}{\frac{2}{\sqrt{3}}}\end{pmatrix}^2 + \begin{pmatrix}\frac{y}{2}\end{pmatrix}^2\\
> \end{align}
> 
> \begin{align}
> \mathcal{C}_0(f_0) : &  2x + y = 0 \\
> & (0,0) \in \mathcal{C}_0(f_0)\\
> & \overrightarrow{n}\begin{pmatrix} 2\\ 1\end{pmatrix} \overrightarrow{u}\begin{pmatrix} -1\\ 2\end{pmatrix}
> \end{align}
> 
> $\min(f_0(xy)) = f_0^*$ pour $(x,y) = (x^*,y^*)$
> $3x^{*2} +y^{*2} = 4$ $(x^*,y^*) \in \mathcal{C}_4(f)$
> $2x^{*} + y^* = f_0^*$ $(x^*,y^*) \in \mathcal{C}_{f_0^*}(f_0)$
> 
> :::info
> \begin{align}
> \Delta f(x^*, y^*) = \begin{pmatrix} 6x^* \\ 2y^*\end{pmatrix}\\
> \langle \Delta f(x^*,y^*), \overrightarrow{u} \rangle = 0\\
> \begin{pmatrix} 6x^* & 2y^* \end{pmatrix} \begin{pmatrix} -1 \\ 2 \end{pmatrix} = 0 
> \end{align}
> :::
> 
> \begin{align}
> 3x^{*2} + y^{*2} &= 4\\
> -6x^* + 4y^* &= 0 \rightarrow y^* &= \frac{6}{4} x^*\\
> & & = \frac{3}{2}x^*\\
> & &= \frac{6}{\sqrt{21}}
> \end{align}
> $y^* = \frac{6}{\sqrt{21}}$
> 
> $3x^{*2} + (\frac{3}{2}x^{*})^2 = 4$
> $3x^{*2}  + \frac{9}{4}x^{*2} = 4$
> $\frac{21}{4}x^{*2} = 4$
> $x^{*2} = \frac{16}{21}$
> $x^* = \frac{4}{\sqrt{21}}$ ou $-\frac{4}{\sqrt{21}}$
> ![](https://i.imgur.com/MfE89nI.jpg)
> 

## Géometrie différentielle pour les petits

Avec ce qu'on a vu à ce jour on peut chercher à résoudre un problème d'optimisation de la forme suivante
$$
\begin{aligned}
\text{min}\qquad & \overbrace{-x_1-2x_2}^{f_o(x_1,x_2)} \\
\text{sujet à} \qquad &x_1+x_2 \leqslant 5 \\
& -2x_1+x_2 \leqslant 3 \\
& x_1, x_2 \geqslant 0
\end{aligned}
$$

![](https://i.imgur.com/y2TapSp.png)
> Sur la rouge non plus, cf (0.5, 1)
> Tu dépasse a gauche

$\color{red}{\text{Le lieu admissible}}$
$\color{green}{\mathscr{C}_0}:$ Courbe de niveau de $f_0$ passant par $(0,0)$

Afin d'améliorer la valeur objectif du point courant, on cherche un point à la fois dans le lieu admissible et dans le demi-espace, qu'on determine à partir de l'équation de la fonction objectif.

La courbe de niveau de la fonction objectif au point optimal isole le lieu admissible dans la partie + des demi-espaces defini par la  courbe de niveau de la fonction objectif en ce point. le demi-espace est un hyperplan d'appui au lieu admissible.

---
> **Exercice :**
>
> $$
> \begin{aligned}
> \text{min}\qquad & x+y \\
> \text{sujet à} \qquad &x^2+y^2 \leqslant 1
> \end{aligned}
> $$
> Comment trouver les hyperplans d'appui au lieu admissible?
> 
> ![](https://i.imgur.com/MbGpHe5.png)
> point optimal en $(\frac{1}{\sqrt{2}}, \frac{1}{\sqrt{2}})$
> je propose
> ![](https://i.imgur.com/AIZviNO.png)
> $\color{blue}{\text{Point optimal B}}$



Quand on cherche à minimiser une fonction objectif affine contrainte par un lieu admissible qui est une ellipse de $\mathbb R^2$, on se retrouve à rechercher des hyperplans d'appui de celui-ci .
Cette notion nous ramene à l'étude des dérivées de fonction numériques dont les graphes décrivent des morceaux du bord  du lieu admissible. Pour généraliser cette approche, on a besoin de généraliser la notion de dérivée sur plusieurs variables.

### Normes sur $\mathbb R^2$

Une norme sur $\mathbb R-ev$ est une manière de mesurer la longueur d'un vecteur, tout en préservant un minimum la structure d'ev. Elle permet en particulier de mesurer la distance entre deux points pour la longueur du vecteur qui les relie.

:::success
**Définition :**
Une norme sur $\mathbb R^n$ est une application $||\cdot||: \mathbb{R}^n \longmapsto \mathbb{R}$ telle que

1) $||x|| = 0 \Longleftrightarrow x = 0$
2) $\forall \lambda \in \mathbb R , \forall x \in \mathbb R^n: ||\lambda x|| = |\lambda|\cdot||x|| \qquad \quad$ (relation d'homogéinité)
3) $\forall x, y \in \mathbb{R}^n$, $||x+y||\leqslant ||x|| + ||y|| \qquad \qquad$ (inégalité triangulaire)
:::

> **Exercice :** sur $\mathbb R^n$
> 
> 1. $||x||_1 = \displaystyle\sum_{i=1}^{n}|x_i|$
> 2. $||x||_2 = \bigg(\displaystyle\sum_{i=1}^{n}(x_i)^2\bigg)^{\frac 1 2}=\sqrt{x^Tx}$
> 3. $||x||_\infty = \underset{i\in \{1,\dots,n\}}{\max}\{|x_i|\}$
> 4. Pour $p \geqslant 1$,
    > $||x||_p = \bigg(\displaystyle\sum_{i=1}^{n}|x_i|^p\bigg)^{\frac 1 p} \qquad \qquad$ (la norme p)

À partir d'une norme sur $\mathbb R^n$, on va pouvoir définir :

1. Une distance : $\forall x, y \in \mathbb R^n, d(x, y) = ||x-y||$

![](https://i.imgur.com/IqsTRki.png)

2. Une notion de voisinage d'un point

    Quand on fait de l'analyse, on s'intéresse à ce qui se passe autour d'un point donné     $\epsilon$-près. Par example, pour montrer qu'une suite numérique $(u_n)_{n\in \mathbb{N}}$ converge vers $l\in \mathbb{R}$, on vérifie:
    $$\forall \epsilon > 0, \exists N \in \mathbb{N}, n \ge N \Longrightarrow \underbrace{|u_n - l| < \epsilon}_{u_n\in ] l-\epsilon, l+\epsilon [}$$
   

La notion de norme sur $\mathbb R^n$ permet de généraliser cette notion à toute dimension. Par exemple si $(u_n)_{n \in \mathbb{N}}$ une suite à valeurs dans $\mathbb R^n$ et $l = (l_1, .., l_n) \in \mathbb{R}^n$.
On dit que (u_n) converge vers l au sens de la norme $||.||$ si :
$$(E) \qquad \forall \epsilon > 0, \exists N \in \mathbb{N}, n \ge N \Longrightarrow |u_n - l| < \epsilon$$

On note
$\begin{aligned}B_{||\cdot||}(l,\epsilon)=\{x\in \mathbb{R}^n | ||x-l||<\epsilon\} \\ \bar{B}_{||\cdot||}(l,\epsilon)=\{x\in \mathbb{R}^n | ||x-l||<\epsilon\} \end{aligned}$


Dans ce cas, $(E)$ s'écrit : 
$$\forall \epsilon > 0, \exists N \in \mathbb N , b \ge N \Rightarrow \mathcal U_n \in B_{||.||}(l,\epsilon)$$

Dans le cas de $\mathbb R^2$ on represente $\overline{B_{||\cdot||}}(\underbrace{\underline{0}}_{\text{l'origine}},1)$

![](https://i.imgur.com/vxTQU9I.png)
![](https://i.imgur.com/WB5lwF8.png)



:::warning
Remarque: les boules d'une norme sont convexes.
du coup, les boules de Noel aussi #loul
:::

Comme on a peu le voir pour la cas de la convergence d'une suite se donner une norme sur $\mathbb{R}^n$ va nous permettre de transposer les notons de continuité d'une fonction ou de comparaison de fonctions en un point $(o, O, \text{~} )$

> **Exercice :**
> On se donne une norme $||.||$ sur$\mathbb R^n$.
> continuite): Soit $f:(E, ||.||_E)\rightarrow (F, ||.||_F)$
> on dit que f est continue en $a \in E$ si 
> * $f$ est défini au voisinage de $a$ 
> $$
> \forall \epsilon > 0, \exists \mu > 0 tq
> ||x-a|| < \mu \Rightarrow ||f(x) - f(a)|| < \epsilon
> $$
>
> $(\theta)$ Une fonction f est un $\theta_1(g)$ en a $\in$ E s'il existe $\epsilon$ :(E,$||\cdot||_E$) $\rightarrow \mathbb R$ telle que
> * $f=\epsilon g$
> * $\epsilon \xrightarrow[a]{} 0$
> 
> Quand g n'est pas identiquement nulle au voisinage de a, la condition précédente est équivalente à $\frac{||f||_F}{||g||_F} \xrightarrow[a]{} 0$

Il semble à ce stade que la définition de continuité ou celle de convergence dépende de la norme choisie.

:::success
**Définition :**
Les normes $||\cdot||_\alpha$ et $||\cdot||_\beta$ sur $\mathbb{R}^n$ sont dites équivalentes s'il existe $c, C \in \mathbb{R}_+^*$ telle que
$$\forall x \in \mathbb{R}^n, c||x||_\alpha \leqslant ||x||_\beta \leqslant C||x||_\alpha$$
Si 2 normes sont équivalentes alors elles définissent les mêmes fonctions continues, les mêmes o, $\theta$, ~ ou encore les mêmes suites convergentes.
:::

:::info
**Théorème :**
Sur $\mathbb R^n$ toutes les normes sont équivalentes.
:::














