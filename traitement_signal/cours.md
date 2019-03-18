# Introduction au traitement du signal

Retour sur le cours de math du signal de l'année d'ing1. (RIP: Siarry)
Comme vous allez voir, il y a deux facettes à ce cours. il y a un volet assez thérorique, scolaire (on va essayer de démystifier la transformée de fourrier), ainsi qu'une séries d'exemples un peu simplistes, concrets, avec lesquels on va jouer.

**[Support de cours](http://www.lrde.epita.fr/~gtochon/MASI/)**

## Introduction 

### Qu'est ce qu'un signal ?


> Ce sont des **phénoménes physiques** mesurable par un capteur, transportant de l'information dans l'*espace* et le *temps*.

Exemple :
* C'est une fonction
* Une onde (électromagnétique / lumière)
* Courant / tension
* Pression / température


:::info
Nous faisons la distinction entre continu et discret.
:::

**Signal analogique** :
> Dépend continuellement de ses variables.

**Signal numérique** :
> Un signal discret est capturé par un capteur, il devient numérique.

Le traitement du signal est né durant la seconde guerre mondiale. Un de ses pères fondateur est Claude Shannon. Il a fondé d'un point de vue mathematique la theorie du signal.
ex: un téléphone utilise continuellement des algo de traitement de signal.

:::info
Si l'on s'arrête aux images, (classe restreinte) on peut voir des application medicales, militaires, etc...
:::

**Question :** Pourquoi le son est échantilloné 44.1kHz ?

> Théorème de shannon: il faut que le signal soit echantillonné à une fréquence deux fois plus importante que la fréquence maximale cible (l'oreille humaine entend jusqu'a 20kHz, donc on échantillonne le son à 44kHz).

### Comment fonctionne une oreille ?

**[Explication ouïe e-penser <3](https://www.youtube.com/watch?v=i2bKuw011nk)**

![Schéma Oreille](https://img-3.journaldesfemmes.fr/ecwoCOyevynOUsgpS0zIox4TF5Q=/427x/smart/1f2336d93ec144d8b53c976108f57ea8/ccmcms-jdf/1155604.jpg)


Les vibration mécanique du son sont transformer en impulsion electrique par la cochlée. En fonction de la fréquence de l'onde des cellules cillié différentes vont être activé.

:::success
Donc l'oreille fait une transformée de fourier...
:::



## Signal

La manière génerale de définir un signal, c'est 3 variables de position et 1 variable de temps, mais pour les besoins de ce cours, on ne travaillera qu'avec 1 seule dimension spaciale.

**Signal :**
> Fonction dépendant d'une seule variable de temps $t$ (avec $t \in \mathbb{R}$)

On mesure une certaine quantite unidimensionnelle a valeur dans $\mathbb{R}$ ou $\mathbb{C}$

:::info
Rappel sur les complexes:
$|z|^2 = z * \bar{z}$
:::


Le signal est un module borné. 
:::info
$\bar{\mathbb{R}} = \mathbb{R} \cup \{+\infty; -\infty\}$
:::


On va autoriser potentiellement des discontinuites.
x est continu ou possède un nombre fini / indénombrable de discontinuités.

Si $x_1$ signal et $x_2$ signal et $\lambda \in \mathbb{R}/\mathbb{C}$ alors $x_1 + x_2$ est un signal.

C'est un espace vectoriel.

En pratique dans cet espace vectoriel on va pouvoir definir:
* une base
* un produit scalaire
* une norme 

### Fonctionnement du radar

> Une onde se propage puis va buter contre un obstacle et refléchi un signal vers l'émeteur.

L'operation qui mesure la ressemblance entre 2 element est le produit scalaire. 

## Produit scalaire

$$
    x = \begin{pmatrix}x_1\\x_2\end{pmatrix}\\
    y = \begin{pmatrix}y_1\\y_2\end{pmatrix} \\
    \langle x,y \rangle = x_1 \times y_1 + x_2 \times y_2 = ||x|| . ||y||.cos(\theta) = \sqrt{x_1^2 + x_2^2}
$$

Si $x,y \in\mathbb{R}^n$ c'est pareil.

$$
    x = \begin{pmatrix}x_1\\\vdots\\x_n\end{pmatrix}\\
    y = \begin{pmatrix}y_1\\\vdots\\y_n\end{pmatrix} \\
    \langle x,y\rangle  = x_1 \times y_1 + ... + x_n \times y_n = \sum_{i=1}^nx_i y_i = x^Ty=(x-x_n)\begin{pmatrix}y_1\\\vdots\\y_n\end{pmatrix}
$$

Si $x,y \in\mathbb{C}^n$.

Produit hermitien (équivalent complexe du produit scalaire):
:::info
$\langle x, y  \rangle$ = $\sum_{i=1}^nx_i \bar{y_i} = x^T\bar{y}$ 
:::


**Définition:** Soit $E$ un espace vectoriel sur $\mathbb{R}$

> $$
\begin{align}
    \langle :\rangle  : &  E \times E \rightarrow \mathbb{R} \\
          & (x, y) \rightarrow \langle x,y\rangle 
\end{align}
$$


1) Symetrie $$\forall x,y \in E : \langle x,y\rangle  = \langle y,x\rangle $$
2) Bilinearite $\forall x,x_2, y \in \mathbb{E} \langle x,y\rangle  = \langle y,x \rangle + \lambda \langle x_2,y \rangle$
3) Positivité: $\forall x \in E, \langle x,x\rangle  \geq 0$
4) Définition: $\langle x,x\rangle =0 \Longleftrightarrow x=0_E$

Si produit hermitien

* Symétrie hermitienne: $\langle x,y \rangle = \bar{ \langle y,x \rangle}$
* Semilinéarité: $$\langle x_1+\lambda x_2,y \rangle= \langle x_1,y \rangle + \lambda \langle x_2, y \rangle\\
                   \langle x,y_1 + \lambda y_2 \rangle = \langle x,y_1 \rangle + \lambda \langle x,y_2 \rangle$$


Norme sur E : $$\begin{align}
                    ||.|| : & E \rightarrow \mathbb{R}^+ \\
                            & x \rightarrow ||x||
                \end{align}$$

1) Séparation : $||x|| = 0 \leftrightarrow x = 0_E$



2) Homogeneite $\forall \lambda \in  R / C  || \lambda x = |\lambda||. ||x||$
3) Inégalité triangulaire: $\forall x,y \in E ||x+y|| \leq ||x|| + ||y||$


On peut définir une norme à partir d'un produit scalaire: $||x|| = \sqrt{\langle x,x\rangle}$

Inégalité de Cauchy Schwarz: $|\langle x,y \rangle| \leq ||x||.||y||$

On peut définir une distance à partir d'une norme : 
$$d(x,y)=\sqrt{\langle x-y,x-y \rangle}$$


On veut définir un produit scalaire entre signaux / fonctions


$$\langle x,y \rangle=x^Ty = \sum_{i=1}^nx_iy_i\\
\begin{pmatrix}x_1\\\vdots\\x_n\end{pmatrix} \in \mathbb{R}^n$$

Avec des éléments continus, $\sum$ va devenir $\int$

Une fonction $x : I \rightarrow R / C$ est integrable sur $I$ ssi $\int_I x(t) dt \langle +\infty$

* $\mathcal{L}^1(I) =$ espace des fonctions intégrables sur $I$
* $\mathcal{L}^P(I) =$ espace des fonctions p-intégrables sur $I$

Si $I=\mathbb{R}$ et $p=2$ $\mathcal{L}^2(\mathbb{R})=$ espace des fonctions de carré intégrable

Ensemble des signaux d'énergie finie :
$x \in \mathcal{L}^2(\mathbb{R}) \Longleftrightarrow \int_\mathbb{R} |x(t)|^2 dt \langle +\infty$ (energie du signal)


Dans $\mathcal{L}^2 , \langle x,y \rangle = \int_{\mathbb{R}} x(t) \bar{y(t)}$ 


Si $x, y$ à valeurs réelle $$\langle x,y \rangle=\int_\mathbb{R}x(t) y(t) dt\\
E_x = \int_\mathbb{R}|x(t)|^2dt = \int_{\mathbb{R}}x(t)\overline{x(t)}dt=\langle x,x \rangle||x||^2=E_x$$
:::info
Définition de la fonction d'inter corrélation entre $x_{ref}$ et $y$

$$ \Gamma_{x_{ref}y}(\tau) ~ =  ~ \langle x_{ref}(t),y(t-\tau)\rangle ~ = ~ \int{_\mathbb{R}x_{ref}(t)\overline{y(t-\tau)} dt}$$

$y(t-\tau)  = y(t)$ retardé d'un facteur $\tau$
$y_\tau(t)  = y(t-\tau)$
$y_\tau(0)  = y(-\tau) \Longleftrightarrow y(0)=y_\tau(\tau)$

:::
 
 



### Autocorrélation de x :

$$x \in \mathcal{L}^2 (\mathbb{R}), \Gamma_{xx}(\tau) ~ = ~ \langle x(t), x(t - \tau)\rangle = \int_{\mathbb{R}}x(t) \overline{x(t - \tau)} dt$$


* 1^er^ propriété 
  * $\Gamma_{xx}$ est maximale pour $\tau=0$
  * $\Gamma_{xx}(0) = \langle x(t),x(t)\rangle = \int_\mathbb{R}(x(t)^2)dt = ||x||^2 = \bar{\tau}_x$ car $\sqrt{ \langle x(t),x(t)\rangle} = ||x||$


* 2^éme^ propriété
    * $\Gamma_{xx}(\tau) = \overline{\Gamma_{xx}(\tau)}$ symetrie hermitienne
    * Si x est à valeurs réelles : $\Gamma_{xx}(- \tau) = \Gamma(\tau)$ : l'autocorrélation est paire

* 3^éme^ propriété
    * $\forall \tau \in \mathbb{R}, |\Gamma_{xx}(\tau)| \leq \Gamma_{xx}(0)$

* Si $x$ est T-périodique : $x(t - \tau) = x(t)$
  $\Gamma_{xx}(T)  = \langle x(t), x(t - \tau) \rangle ~ = ~ \langle x(t),x(t)\rangle ~ = ~ \Gamma_{xx}(0)$
  $\Gamma_{xx}$ est périodique


---

### Intercorrélation

> On va peu faire d'autocorrélation, on va travailler avec de l'**intercorrélation**.
> Au lieu de comparer la ressemblance entre x et x retardé, on va comparer x et y.

Intercorrelation de 2 signaux $x, y \in \mathcal{L}^2(\mathbb{R})$, $y(t)=x(t-t_0)$ :

\begin{align}
\Gamma_{xy}(\tau) &= \langle x(t), y(t-\tau)\rangle = \int_\mathbb{R}x(\tau)\overline{y(t-\tau)}dt\\
&= \langle x(t), y(t-\tau)\rangle \\
&= \langle x(t),x((t-t_0)-\tau)\rangle\\
&= \underbrace{\langle x(t), x(t-(t_0 + \tau))\rangle}_{\Gamma_{xx}(t_0-\tau)}
\end{align}



\begin{align}O_x \Gamma_{xx}\text{ est maximale en } & 0 = t_0 + \tau  \\
& \tau = - t_0\end{align}


:::success
Donc $\Gamma_{xy}$ est maximale en $- t_0$
:::	

$$y(t) = x(t) + \eta(t) \thicksim \mathcal{N}(0,\sigma^2)$$

\begin{align}
\Gamma_{xy}(\tau) &= \langle x(t), y(t - \tau) \rangle \\
&=\langle x(t), x(t-\tau) + \eta_\sigma (t - \tau) \rangle \\
&= \langle x(t), x(t-\tau) \rangle +  \langle x(t), \eta_\sigma (t - \tau) \rangle\\
&=\Gamma_{xx}(\tau)\\
&=E[X \eta_\sigma] = E[X] E[\eta_\sigma] = 0
\end{align}


Si $x$ et $y$ sont 2 variables independantes alors $E[xy] = E[x] E[y]$

## Convolution

> C'est l'opération mathématique derriere tous les filtrages.[name=Tochon]

Soit $f,g \in \mathcal{L}^1(\mathbb{R})$.

On appelle produit de la convolution de $f$ et de $g$ l'opération :
$$(f * g)(t) = \int^{+\infty}_{-\infty}f(x)g(t-x)dx
= \int^{+\infty}_{-\infty} g(x)f(t -x)dx
$$

> La convolution c'est "juste" une moyenne pondérée glissante généralisée [name=Tochon]

#### Propriétés :

1) Existence du produit de convolution :
  Pour que $x * y$ existe, il suffit que $x,y \in \mathcal{L}'(\mathbb{R})$
  Auquel cas, $(x * y) \in  \mathcal{L}^1(\mathbb{R})$
  Rappel: $x \in \mathcal{L}'(\mathbb{R}) \Leftrightarrow \int_\mathbb{R}|x(t)|dt < + \infty$

2) Le produit de convolution est commutatif : $(x * y) = (y * x)$
3) Le produit de convolution est bilinéaire : $x * (y + \lambda z) = (x*y) + \lambda (x * z)$
4) Le produit de convolution est associatif : $(x*y)*z = x*(y*z)$
5) Le produit de convolution admet un élement neutre. Le delta de Dirac :
$$\delta : t \rightarrow 
\begin{cases}
    0 ~ \forall t \neq 0 \\ 
    +\infty t = 0 
\end{cases} \\
\int_\mathbb{R} \delta(t)dt = 1
$$

:::success
$\mathcal{L}^1(\mathbb{R})$ munit du produit de convolution forme donc un monoïde commutatif.
:::

#### Symetrie :

Si $x$ et $y$ sont des signaux soit pairs soit impairs. $(x * y)$ est  paire ssi $x$ et $y$ sont de même parite.

$(x*y)$ est impaire ssi $x$ et $y$ sont de parité opposés.

#### Dérivée:

Si $x, y  \in \mathcal{L}'(\mathbb{R})$ et sont derivables avec $x',y' \in \mathcal{L}'(\mathbb{R})$

$(x*y)'=x'*y=x*y'$

#### Fonction porte

$\Pi_T(t)=\begin{cases}1 ~\forall t\in [-\frac{T}{2}; \frac{T}{2}] \\ 0 ~ \text{sinon}\end{cases}$

![Représentation fonction porte](https://proxy.duckduckgo.com/iu/?u=https%3A%2F%2Ftse1.mm.bing.net%2Fth%3Fid%3DOIP.Dfqwz-iTOmojUspk9cLrJwHaFH%26pid%3D15.1&f=1) 

[Elle est fausse, la notre vaut 1 aux bornes. TODO]


\begin{align}
(\Pi_{T} * \Pi_{T} )(t) &= \int_{\mathbb{R}} \underbrace{\Pi_{T}(x)}_{0 \text{ si } x \notin [-\frac{T}{2};\frac{T}{2}]} \Pi_{T}(t -x)dx \\
                        &= \int_{-\frac{T}{2}}^{\frac{T}{2}}\Pi_T(t-x)dx
\end{align}

* Pas de chevauchement $\Leftrightarrow |t| > T$ 
* Chevauchement max $t = 0$

$$(\Pi_T * \Pi_T)(0)=\int_{-\frac{T}{2}}^{\frac{T}{2}} 1 dx = T$$

* Si $0 < t < T$

$$(\Pi_T * \Pi_T)(t)=\int_{t-\frac{T}{2}}^{\frac{T}{2}}dx = \frac{T}{2} - (t - \frac{T}{2}) = T - t$$

* Si $-T < t < 0$
$(\Pi_{T} * \Pi_{T})(t) = \int_{\frac{-T}{2}}^{t + \frac{T}{2}}dx = t+ \frac{T}{2} +\frac{T}{2}$

:::warning
Ca été donné au partiel de MASI des Ing1. Donc ca sera potentiellement à notre partiel.
:::



$$\Gamma_{xy}(\tau) = \langle x(t), y(t-\tau)\rangle = \int_\mathbb{R}x(\tau)\overline{y(t-\tau)}dt\\
(x * y)(\tau) = \int_\mathbb{R}x(t)y(t-\tau)dt\\
y^-(t)=y(-t)$$
\begin{align}
(x*y^-)(\tau) &= \int_\mathbb{R}x(t)y^-(\tau - t)dt\\
              &= \int_\mathbb{R}x(t)y(t - \tau)dt\\
\end{align}

$$(x*\bar{y})(\tau)=\int_\mathbb{R}x(x(t)\overline{y^-(\tau - t)}dt) = \int_\mathbb{R}x(t)\overline{y(t - \tau)}dt=\Gamma_{xy}(\tau)
$$

:::success
$$\Gamma_{xy}  = (x * \overline{y^{-}})$$
:::

:::info
**Convolution filtrage :** opération mathématique produit de convolution
**Corrélation :** motif dans un signal
:::

> On ne peut pas faire pire qu'un cours de Siarry [name=Tochon]

## Série de Fourier

:::info
Né au milieu du 18ème siecle, doit son nom à Fourier pour résoudre une équation de la chaleur (comment la chaleur se propage dans une barre)
Travaux début 1800, les premiers résultats mathématiques sont en 1830.
:::

Un phénomene vibratoire peut se séparer en superposition de phénomène vibratoire.
> Exemple: la lumière blanche qui se décompose en beaucoup de longueurs d'ondes différentes.


### Principe de superposition:

> Décomposition d'un phenomene vibratoire complexe en une superpostion de phénomènes vibratoires simples.

* Sytème vibratoire complexe: Signal périodique de periode T.
* Systeme vibratoire simple: Onde sinusoidale $A \sin(2\pi ft + \phi)$

$\sin(x) \rightarrow \text{periode } 2 \pi$

![Sinus function](https://www.mathsisfun.com/algebra/images/sine-graph.svg)

Calcul de période:
* $\sin(\frac{2\pi}{T}x) \Rightarrow T$
* $\sin(2\pi\frac{n}{T}x) \Rightarrow \frac{T}{n}$
* $\sin(2\pi x) \Rightarrow 1$
* $\sin(x) \Rightarrow 2\pi$

$$\begin{align}
x(t) &= \sum^{N}_{n=1} A_n \sin(2\pi\frac{n}{T}t + \phi_n) \\
     &= A_1 \sin(\underbrace{\frac{2\pi}{T}}_{\text{fréquence fondamentale } f = \frac{1}{T}} t+d_1) + \dots + A_N \sin(2\pi \frac{N}{T}t + \phi_N)
\end{align}$$

:::info
**Notations :**
* $w = \frac{2\pi}{T} =$ pulsation
* $f =$ fréquence
* $T = \frac{1}{f} =$ période
:::
---

:::info
**Rappels :**
$\sin(a + b) = \sin a \cos b + \cos a \sin b$
$\cos(a + b) = \cos a \cos b - \sin a \sin b$
:::

\begin{align}
x(t) &= a_0 + \sum^{N}_{n = 1} A_n[\sin(2 \pi \frac{n}{T} t) \cos(\phi_n) + \cos(2 \pi \frac{n}{T} t) \sin (\phi_n)]\\
&= a_0 + \sum^{N}_{n = 1} A_n \sin(\phi_n) \cos(2 \pi \frac{n}{T} t) + A_n \cos(\phi_n) \sin(2 \pi \frac{n}{T} t) \\
&= a_0 + \sum^{N}_{n = 1}a_n  \cos(2  \pi \frac{n}{T}  t) + b_n  \sin(2  \pi  \frac{n}{T}  t )
\end{align}


#### Decomposition des termes

$$S_n = \sum_{n = 1}^{+\infty} a_n \cos(2\pi \frac{n}{T} t) + b \sin(2\pi \frac{n}{T} t)$$

$S_1 = a_1 \cos(2\pi \frac{1}{T} t)$
$S_2 = a_1 \cos(2\pi \frac{1}{T} t) + a_2 \cos(2\pi \frac{2}{T} t)$

---


$x(t) = a_0 + \sum_{n = 1}^{+\infty} a_n \cos(2 \pi \frac{n}{T}t) + b_n \sin(2\pi \frac{n}{T}t)$

> Comment déterminer ces coefficients : $a_0, \{a_n, b_n\}_{n \geq 1}$ ?

#### Lemme #1

Soit x une fonction T-périodique

\begin{align}
\int_0^T x(t)dt &= \int_a^{a + T} x(t)dt ~ \forall a \\
                &= \int_{-\frac{T}{2}}^{\frac{T}{2}} x(t)dt
\end{align}


#### Lemme #2

$$\int_{0}^{T} \cos(2\pi \frac{n}{T} t) \cos(2\pi \frac{k}{T}t)dt =
\int_{-\frac{T}{2}}^{\frac{T}{2}} \cos(2\pi \frac{n}{T} t) \cos(2\pi \frac{k}{T}t)dt =
\begin{cases}0 ~ n\neq k\\\frac{T}{2} ~ n = k\end{cases}$$

#### Lemme #3
$$\int_{0}^{T} \sin(2\pi \frac{n}{T} t) \sin(2\pi \frac{k}{T}t)dt =
\int_{-\frac{T}{2}}^{\frac{T}{2}} \sin(2\pi \frac{n}{T} t) \sin(2\pi \frac{k}{T}t)dt =
\begin{cases}0 ~ n\neq k\\\frac{T}{2} ~ n = k\end{cases}$$

:::info
**Rappel :**
$\cos a \cos b = \frac{1}{2} (\cos (a+b) + \cos(a - b))$
:::


#### Preuve du lemme #2

* Si $n \neq k$ :
$$
\int_{0}^{2\pi} \cos(nt) * \cos(kt) dt =  \int_{0}^{2 * \pi} 1 / 2 * (\cos(n + k)t) + \cos((n - t)t) dt\\ 
\frac{1}{2} \int_0^{2\pi} \cos((n + k)t)dt + \frac{1}{2} \int_0^{2\pi} \cos((n - k)t)dt \\
= \frac{1}{2} [\frac{1}{n +k} \sin((n + k)t)]_{0}^{2\pi} + \frac{1}{2}[\frac{1}{n - k} \sin ((n - k)t)]_0^{2\pi}\\ 
= \frac{1}{2} \frac{1}{n+k}(\underbrace{\sin((n+k)2\pi)}_{=0} - \underbrace{\sin((n+k)0)}_{=0} + \dots = 0
$$

* Si $n = k$ :
$$
\cos^2(a)=\frac{1+\cos(2a)}{2} \\
\int_0^{2\pi}\cos^2(nt)dtA \\
= \int_0^{2\pi}\frac{1+cos(2nt)}{2}dt
= \int_0^{2\pi}\frac{1}{2}dt + \int_0^{2\pi}\frac{cos(2nt)}{2}dt \\
= \frac{1}{2}\int_0^{2\pi}cos(2nt)dt
= \frac{1}{2}[\frac{1}{2n}\sin(2nt)]^{2\pi}_0 = 0
$$


#### Lemme #4

$$
\int_{0}^{T} (\cos(2\pi * \frac{n}{T} t) * sin(2\pi * \frac{k}{T}t)  dt))
$$


On suppose toujours que $x(t) = a_0 + \sum_{n = 1}^{+\infty} a_n \cos(2\pi\frac{n}{T}t) + b_n \sin(2\pi \frac{n}{T}t)$

$a_0$: On integre entre $0$ et $T$


\begin{align}
\int_0^T x(t) dt &= \int_0^T [a_0 \cos(2\pi \frac{n}{T}t) + b_n \sin (2\pi \frac{n}{T})]dt\\
                  &= \int_0^T + \sum_{n = 1}^{+\infty} \int_0^T a_n cos(2\pi \frac{n}{T}) dt )\\
                  &= T a_0 + \sum^{+\infty}_{n=1}a_n\underbrace{\int_0^T\cos(2\pi \frac{n}{T}t)dt}_{=0} + \sum_{n=1}^{+\infty}b_n \underbrace{\int_0^T\sin(2\pi\frac{n}{T}t)dt}_{=0}
\end{align}


$a_0 = \frac{1}{T} \int_0^T x(t)dt \equiv$ valeur moyenne de $x$ sur une periode  

---

$\{a_n: n \geq 1\}$: On cherche $a_k$, $\forall k \in \mathbb{N}^*$


On multiplie par $\cos (2\pi \frac{k}{T}t)$ l'egalite puis on integre entre 0 et T.

\begin{align}
x(t)cos(2\pi \frac{k}{T}t) &= a_0 \cos(2\pi \frac{k}{T}t) + \sum_{n+1}^{+\infty} a_n \cos(2\pi \frac{n}{T}t) \cos(2\pi \frac{k}{T}t) + b_n \sin(2\pi \frac{n}{T}t) \cos(2\pi \frac{k}{T}t)\\
\end{align}




\begin{align}
\int_0^T x(t) cos(2\pi t\frac{k}{T}) dt &= a_0 \int_0^T cos(2\pi tk/T) dt \\
                                        &\underbrace{+ \sum_{n=1}^{+\infty}a_n + \int_{n = 1}{+\infty}\sin(2n * \frac{n}{T})\cos(2n \frac{k}{T}t) dt}_{\text{tous les termes sont nuls sauf le $k^{ième}$, qui vaut $a_k \frac{T}{2}$}}\\
                                        = a_k \times \frac{T}{2}
\end{align}



$a_n = \frac{2}{T} \int_0^T x(t) \cos(2\pi \frac{n}{T}t)dt \: \forall n \ge 1$
Et $b_n = \frac{2}{T} \int_0^T x(t) \sin(2\pi \frac{n}{T}t)dt \: \forall n \ge 1$

### Fonction continue par morceaux sur un intervalle $[a,b]$

$x \in \mathcal{C}_{pm}^o ([a,b])$ si $x$ est continue sur $[a,b]$, sauf a un certain nombre de points de discontinuité $a_i$, tq $x(a_i)=\lim_{t \rightarrow a;\\t < a;} x(t)$


et $x(a_i^+) = \lim_{t \rightarrow a;\\ t > a;}  x(t)$ mais potentiellement $x(a_i) \neq x(a_i^-) \neq x(a_i^+)$

![fonction discontinue](https://proxy.duckduckgo.com/iu/?u=http%3A%2F%2Fupload.wikimedia.org%2Fwikipedia%2Fcommons%2F0%2F0e%2FFonction_discontinue.png&f=1)

Fonction dérivable par morceaux $(\mathcal{C}^1_{pm})$ sur $[a,b]$
* $x$ dérivable sur $[a,b]$ sauf éventuellement en un certain nombre de points pour lesquels il est possible de définir des limites à gauche et à droite de la derivée.


#### Théoreme de Dirichlet

Soit un signal T-périodique et $\mathcal{C}^1_{pm}$. Alors en tout point de continuité de $x$, on a :
$\displaystyle x(t) = a_0 + \sum_{n = 1}^{+\infty} a_n \cos(2\pi \frac{n}{T}t) + b_n \sin(2\pi \frac{n}{T}t)$

Si $x$ discontinue en $t_0$:
$$
a_0 + \sum^{+\infty}_{n=0}a_n \cos(2\pi \frac{n}{T}t_0) + b_n \sin(2\pi \frac{n}{T}t_0) = \frac{1}{2}(x(t_0^-) + x(t_0^+))\\
$$
avec
\begin{align}
a_0 &= \frac{1}{T} \int_0^Tx(t)dt\\
a_n &= \frac{2}{T} \int_{0}^T x(t) \cos(2 \pi \frac{n}{T}t)dt\\
b_n &= \frac{2}{T} \int_{0}^T x(t) \sin(2 \pi \frac{n}{T}t)dt\\
\end{align}

### Transformee de Fourier

$$
\underbrace{x(t)}_{\text{periode } T} \underbrace{=}_{\text{*cf dessous} } a_0 + \sum_{n = 1}^{+\infty} a_n \cos(2\pi \frac{n}{T}t) + b_n \sin(2\pi \frac{n}{T}t)
$$

$\text{*}$ theoreme de Dirichlet: x doit etre $\mathcal{C}^1$ par morceau a tout point de continuité de x. Si discontinuen t_0, alors la Serie de Fourier converge vers $\frac{1}{2} (x(t_0^-) + x(t_0^+))$

$$
a_0 = \frac{1}{T} \int_0^{T}x(t)dt\\
a_n = \frac{2}{T}\int^T_0 x(t) \cos(2\pi \frac{n}{T}t)dt , n \ge 1\\
b_n = \frac{2}{T} \int^T_0 x(t) sin(2\pi \frac{n}{T}t)dt , n \ge 1 \\
$$


> **Exercice:**
> Calculer les coeficient de la série de fourier du signal en crénaux.
> ![](https://upload.wikimedia.org/wikipedia/commons/thumb/6/68/Signal_creneau_symetrique.svg/1200px-Signal_creneau_symetrique.svg.png)
> signal centre en $\frac{1}{2}$ et avec Ym = 1 et -Ym = 0
> 
> * $a_0 = \frac 1T \int_0^T x(t)dt = \frac 1T \int_0^{\frac T2}dt = \frac 12$
> * $a_n = \frac 2T \int_0^T x(t)\cos(2\pi \frac nTt)=\frac 2T \int_0^{\frac T2}\cos(2\pi \frac nT t)dt\\ = \frac 2T \frac{T}{2\pi n}[\sin(2\pi \frac nTt)]^\frac T2_0 = \frac{1}{t /n}(\sin(tn)-sin(0))=0 \qquad\forall n \geq 1$
> * $b_n = \frac 2T \int_0^T x(t)\sin(2\pi \frac nT t)dt = \frac 2T \int_0^{\frac T2}\sin(2\pi \frac nTt)dt\\=-\frac 2T \frac{T}{2\pi n}[\cos(2 \pi \frac nTt)]_0^{\frac T2} = - \frac{1}{\pi n}(\cos(n\pi)-\cos(0))=\frac{1}{\pi n}(1-\cos(n\pi))$
> $b_n = \frac{1}{\pi n}(1-(-1)^n)=\begin{cases}0 \text{ si n pair}\\ \frac{2}{\pi n}\text{ si n impair}\end{cases}$
>
>\begin{align}
> x(t)&= a_0 + \sum_{n = 1}^{+\infty} a_n \cos(2\pi \frac{n}{T}t) + b_n \sin(2\pi \frac{n}{T}t)\\
> &=\frac{1}{2} + \sum_{\underbrace{n = 1}_{n \text{ impair } \rightarrow  n = 2k +1}}^{+\infty} b_n \sin(2\pi \frac{n}{T}t)\\
> &= \frac{1}{2} + \sum^{+\infty}_{k = 0} b_{2k + 1} \sin(2 \pi \frac{(2k + 1)}{T} t)\\
> & =\frac{1}{2} + \sum^{+\infty}_{k = 0} \frac{2}{\pi(2k + 1)} \sin(2\pi \frac{2k+1}{T}t)\text{ en tout point de continuite de x}.
> \end{align}
> Et en $\frac T2$ ?
> * $x(\frac T2) = 1$
> * $x(\frac{T^t}2) = 0$
> * $\sin(2 \pi (\frac{2k+1}{T})\frac T2)= \sin((2k+1)\pi) = \sin(2k\pi + \pi) = \sin(2k\pi + pi) = \sin(\pi) = 0$

$S_N (A) = a_0 + \sum_{n = 1}^{N} a_n \cos(2\pi \frac{n}{T}t) + b_n \sin(2\pi \frac{n}{T}t)$
$x \text{discontinu en }t_0$
$|\Delta x(t_0)|$ hauteur de la discontonuite:
hauteur du sursaut $\rightarrow  \approx 0.09 |\Delta x(t_0)|$


:::info
On a les coefficients on va doucement se rapprocher de la série de fourier.
:::


On va admettre que l'ecriture $x(t)= a_0 + \sum_{n = 1}^{+\infty} a_n \cos(2\pi \frac{n}{T}t) + b_n \sin(2\pi \frac{n}{T}t)$
est équivalente à $x(t)=\sum_{n=-\infty}^{+\infty}C_ne^{i2\pi\frac nTt}$
avec $C_n = \frac 1T \int_0^T x(t)e^{-i2\pi \frac nTt}dt$

:::info
$e^{i\theta} = \cos \theta + i\sin \theta \rightarrow \boxed{e^{i\pi}+1 = 0}$ est stylé car il y a toute les maths
$\cos \theta = \frac{e^{i\theta}+e^{-i\theta}}{2}$
$\sin \theta = \frac{e^{i\theta}-e^{-i\theta}}{2i}$
:::

Si x est pair $\rightarrow b_n = 0 \forall n \ge 1$
Si x est impair $\rightarrow a_n = 0 \forall n \ge 1$


$\{|a_n|, n \in \mathbb{Z}\}$ : spectre du signal
Si le signal est à valeurs réelles $(x(t) \in \mathbb{R})$
$C_{-n} = \overline{C_n} \rightarrow |C_{-n}| = |C_n|$
On peut etudier uniquement les $C_n$ pour n $\ge$ 0

$$\forall n \ge 1 \begin{cases} a_n  = C_n + C_{-n}\\
b_n  = i(C_n - C_{-n})\end{cases}
\Leftrightarrow
\begin{cases} C_n  = \frac{1}{2} (a_n - ib_n)\\
C_{-n}  = \frac{1}{2} (a_n + ib_n)\end{cases}
$$

:::info
Soit $u = \{u_1, \dots, u_n\}$ une base de $\mathbb R^n$ et <;> un produit scalaire sur $\mathbb R^n$
$u$ est une base orthonormée de $\mathbb R^n$ ssi \begin{cases}\langle u_i, u_j \rangle = 0 \quad i \neq j\\ ||u_i|| = 1\end{cases}
:::


cas en 2 dimensions
$$
\overrightarrow{x} = x_1 \overrightarrow{u_1} + x_2 \overrightarrow{u_2}\\
= \langle \overrightarrow{x_1}, \overrightarrow{u_1} \rangle \overrightarrow{u_1} + \langle \overrightarrow{x_1}, \overrightarrow{u_2} \rangle \overrightarrow{u_2}\\
\langle \overrightarrow{x}, \overrightarrow{u_1} \rangle = \langle \begin{pmatrix} x_1 \\ x_2\end{pmatrix} \begin{pmatrix} 1 \\ 0\end{pmatrix}  \rangle = x_1
x_1 =\langle \overrightarrow{x_1}, \overrightarrow{u_1} \rangle = \text{projection de} \overrightarrow{x} \text{ sur l'axe des engendre par } \overrightarrow{u_1}
$$

$$
\overrightarrow{x} = \begin{pmatrix} x_1 \\ ... \\ ... \\ x_n\end{pmatrix} \text{ dans } u\\
\overrightarrow{x} = \sum_{i = 1}^{n} x_i \overrightarrow{u_i} \quad , x_i = \langle \overrightarrow{x_i} , \overrightarrow{u_i} \rangle\\
$$

:::success
$\overrightarrow{x} = \sum_{i = 1}^n \langle \overrightarrow{x} , \overrightarrow{u_i} \rangle \overrightarrow{u_i}$
:::

$x(t) = \sum^{+\infty}_{n = -\infty} a_n e^{i2\pi\frac{n}{T}t}$
$C_n = \frac{1}{T} \int_0^T x(t) e^{-i2\pi \frac{n}{T}t}dt$

$\langle x(t), y(t) \rangle = \frac{1}{T} \int_0^T x(t) \overline{y(t)} dt$
$\langle x(t), y(t) \rangle = \int_{\mathbb{R}} x(t) \overline{y(t)} dt$
On va admettre que $\{ U_n : t \rightarrow e^{i2\pi\frac{n}{T}t, n \in \mathbb{Z}}\}$ forme une base de $\mathcal{L}^2([0,T])$ et on va verifier qu'elle est orthonormee pour $\langle : \rangle$ 




\begin{align}
<u_n(t), u_m(t)> &= \frac{1}{T} \int_0^T  u_n(t) \overline{u_m(t)} dt \\
&= \frac{1}{T} \int_0^T e^{i2\pi \frac{n}{T} t} \overline{e^{i2\pi \frac{m}{T} t}} dt \\
&= \frac{1}{T} \int_0^T e^{i2\pi \frac{n - m}{T} t} dt \\
&= \frac{1}{T} \int_0^T e^{i2\pi \frac{k}{T} t} dt\\
&= \frac{1}{T} \frac{T}{2k\pi} [e^{i2\pi \frac{k}{T} t}]_0^T\\
&= \frac{T}{2ik\pi} (e^{i2k\pi} e^0) = 0
\end{align}


$\langle x,x \rangle = ||x||^2$
$\langle u_n(t) , u_n(t) \rangle = \frac{1}{T} \int_0^T u_n(t) \overline{u_n(t)}dt$
$= \frac{1}{T} \int_{0}^T e^{i 2 \pi \frac{n}{T}t} e^{-i 2 \pi \frac{n}{T}t}dt$
$=$

VOIR PHOTO DESSOUS

![](https://i.imgur.com/VLNVY4D.jpg)


:::info
**L'énergie d'un signal**
\begin{align}
E_x&=\int_\mathbb{R} |x(t)|^2 dt < +\infty\\
   &=\langle x(t), x(t)\rangle
\end{align}

---

Avec $x \in \mathcal L^2([0,T])$
L'énergie de $x$ devient $\underbrace{E_x}_{\text{Energie temporelle}}=\langle x(t), x(t) \rangle = \frac 1T \int_0^T |x(t)|^2 dt$

:::

$|C_n|^2 \equiv$energie de l'harmonique de rang $n$
$\rightarrow$ energie du spectre $=$ somme des energies des harmoniques $\rightarrow \sum_{n = -\infty}^{+\infty} |C_n|^2$

### theorème de Parseval

\begin{align}
\frac{1}{T} \int_{0}^{T} \underbrace{|x(t)|^2}_{\text{energie temporelle}} dt & = \sum_{n = -\infty}^{+\infty} \underbrace{|C_n|^2}_{\text{energie frequentielle}}\\
& = a_0^2 + \sum_{n=1}^{+\infty} (\frac{a_n^2 + b_n^2}{2})
\end{align}


#### exemple

$a_0 = \frac{1}{2}$
$a_n = 0 \forall n \ge 1$
$b_n = \begin{cases} 0 \text{ si n pair} \\ \frac{2}{|pi n} \text{ si n impair}\end{cases}$

$C_n = \frac{1}{2}(a_n - b_n) = \begin{cases} 0 \text{ si n pair} \\ \frac{-i}{\pi n} \text{si n impair}\end{cases} \qquad \qquad n \ge 1$

$|C_n| \underbrace{\sim}_{n \rightarrow \infty} \frac{1}{n}$ pour tous les signaux avec une discontinuité


* Si $x^{(0)}, x^{(1)}, x^{(2)}, x^{(k - 1)}$ sont des signaux continus,  et $x^{(k)}$ a des discontinuites, alors $|C_n| \underbrace{\sim}_{n \rightarrow + \infty} \frac{1}{n^{k + 1}}$ 

$x(t) = \sum_{n=1}^{+\infty} C_n e^{i2\pi \frac{n}{T} t}$
T periodique
$C_n$ coef du $n^e$ harmonique $\rightarrow$ frequence $\frac{n}{T}$
$C_{n+1}$ coef du $(n+1)^e$ harmonique $\rightarrow$ frequence $\frac{n+1}{T}$

"gap" en frequence $\frac{n+1}{T} - \frac{n}{T} = \frac{1}{T}$



#### Signal non periodique

signal periodique de periode infinie (T = $\infty \rightarrow gap$ nul entre deux frequences successives)
$\rightarrow$ etude par la transformee de Fourier $\equiv$  generalisation des series de fourier aux signaux non periodiques

#### Serie de Fourier
:::info
**Definition** : Sous reserve d'existence, la transformee d'un signal  x est la fonction :
\begin{align}
X:\mathbb R \rightarrow \mathbb C\\
\nu \rightarrow \int_{\mathbb R} x(t) e^{-i 2 \pi \color{orange}{\nu} t}dt\\
C_n = \frac{1}{T} \int_{\frac{-T}{2} \rightarrow +\infty}^{\frac{T}{2} \rightarrow +\infty} x(t)e^{-i 2 \pi \color{orange}{\underbrace{\frac{n}{t}}_{\nu}}t}dt 
\end{align}
:::

$F(x(t)) = x(f) = X(\nu)$
$X(\nu)$ existe $\Leftrightarrow |X(\nu) < \infty$

\begin{align}
\forall \nu \in \mathbb R ,|X(0)| &= |\int_{\mathbb R} x(t) e^{-i 2 \pi \nu t}dt|\\
&\le \int_{\mathbb R} |x(t)| \underbrace{|e^{-i 2 \pi \nu t}}_{=1}|dt\\
&\le \int_{\mathbb R}\underbrace{|x(t)|}_{< + \infty}dt
\end{align}



Condition d'existance de la TF:
Si $x \in \mathcal L^1(\mathbb R)$, alors $X$ existe.

Th de Dirichlet : $x(t) = \int_{-\infty}^{+\infty} X(\nu)e^{i2\pi{}\nu{}t} d\nu$
 
:::info
**Transformée de Fourier inverse :** Sous réserve d'existence, on peut inverser la transformée de Fourier : $\boxed{x(t)=\int_{-\infty}^{+\infty} X(u)^{+i2\pi ut}e ~du}$
:::

$F(\Pi_T(t)) = \widehat{\Pi}_T(u)= \int_{\mathbb R_{+\infty}} \Pi_T(t)e^{-i2 \pi ut}~dt=\int_{-\infty}^{+\infty}\Pi_T(t)e^{-i2\pi ut}~dt$
 
 \begin{align}
\widehat{\Pi}_{T}(u) &= \int_{-\frac{T}{2}^{\frac{T}{2}}} e^{-i 2 \pi \nu t}dt\\
&= -\frac{1}{i2 \pi \nu} [e^{-i2\pi\nu t}]_{\frac{-T}{2}}^{\frac{T}{2}}\\
&= -\frac{1}{i2 \pi \nu} (e^{-i2\pi \nu \frac{T}{2}} e^{i2\pi \nu \frac{T}{2}})\\
&=\frac{e^{i\pi \nu T} -e^{-i\pi \nu T} }{i2\pi\nu}\\
&=\frac{1}{\pi\nu}* \frac{e^{i\pi \nu T} -e^{-i\pi \nu T} }{2i}\\
&=\frac{\sin(\pi\nu T)}{\pi\nu}\\
\end{align}
 
:::info
**Sinus cardinal :**
$$sinc:x \mapsto \begin{cases}
\frac{sin(x)}{x} &\qquad x \neq 0\\
1 &\qquad x=0
\end{cases}$$
:::
 
 $\mathcal{F}(\Pi_T(t) = \underbrace{T\underbrace{sinc}_{\text{sinus cardinal}}(\pi \nu T))}_{*schema*}$
 
:::info
dirac 
$\delta(\nu)$ = \begin{cases} \inf \qquad \space \text{ $\nu$ = 0} \\ 0 \qquad \quad \text{ $\nu$ $\neq$ 0}\end{cases}

$\int_\mathbb R \delta(\nu) d\nu = 1$
:::

$$
\delta(t) = \begin{cases} \inf \qquad \space \text{t = 0} \\ 0 \qquad \quad \text{t $\neq$ 0}\end{cases} \qquad et \int_\mathbb R \delta(t)dt = 1
$$

$$
 \equiv \delta(t-t_0) = \begin{cases} \inf \qquad \space \text{t = $t_0$} \\ 0 \qquad \quad \text{t $\neq$ $t_0$}\end{cases}
$$

$$
\alpha \delta_{t_0}(t) = \begin{cases} \inf \qquad \space \text{t = $t_0$} \\ 0 \qquad \quad \text{t $\neq$ $t_0$}\end{cases} \int_\mathbb R \alpha \delta_{t_0}(t)dt = \alpha \int_\mathbb R \delta_{t_0}(t)dt = \alpha
$$

$$
x(t)\delta(t-t_0)=x(t_0)\delta(t-t_0) = \begin{cases} \inf \qquad \space \text{t = $t_0$} \\ 0 \qquad \quad \text{t $\neq$ $t_0$}\end{cases} 
$$
$$
et \int_\mathbb R x(t) \delta(t-t_0)dt = x(t_0)
$$
On "preleve/echantillonne" le signal de x en $t_0$

$x(t) * \delta(t-t_0) = x(t-t_0)$
$t_0 = 0 \rightarrow (x\circ\delta)(t) = x(t)$

:::info
$\mathbb F(1) = \delta(\nu) \qquad \mathbb F(\alpha) = \alpha\delta(\nu)$
:::

$x(t) = \int_{\mathbb R} x(\nu) e^{i 2 \pi \nu t}d\nu \quad (TF inverse)$
$x(-t) = \int_{\mathbb R} x(\nu) e^{i 2 \pi \nu (-t)}d\nu = \int_{\mathbb R} x(\nu) e^{-i 2 \pi \nu t}d\nu = \mathbb F(X(\nu)) = \mathbb F(x(t))$


$\mathbb F(\mathbb F(x(t))) = x(-t)$
si x est pair $x(-t) = x(t)$
$\mathbb F(\mathbb F(x(t))) = x(t)$
$\mathbb F(x(t)) = \mathbb F^{-1}(x(t))$
$\mathbb F(\Pi) = sinc$
$\mathbb F(sinc) = \Pi$

![](https://i.imgur.com/VCDJEwN.jpg)
![](https://i.imgur.com/X8mRJyh.jpg)

Si $x$ est à valeurs réelles, $X(u) = \int_{\mathbb R} x(t) e^{i2\pi\nu t} dt$

\begin{align}
\overline{X(\nu)} &= \overline{\int_{\mathbb R} x(t) e^{-i2\pi \nu t}dt}\\
&= \int_{\mathbb R} \underbrace{\overline{x(t)}}_{x(t)} \underbrace{\overline{e^{-i2\pi \nu t}}}_{e^{-i2\pi \nu t}}\\
&= \int_{\mathbb R}x(t)e^{i2\pi (-\nu) t}dt\\
&= X(-\nu) = \overline{X(\nu)}\\
& (\overline{c_n} = c_{-n} )\\
\end{align}
Le spectre d'un signal reel est pair.

Si x est reel et pair

formule d'euler : $e^{-i\theta}  =cos(\theta) - i*sin(\theta)$

\begin{align}
_{\in \mathbb C} X(\nu) &= \int_{\mathbb R} x(t) e^{i2\pi\nu t} dt \\
&= \int_\mathbb R x(t)(cos(2\pi\nu t) - i*sin(2\pi\nu t)) dt \\
&= \int_\mathbb R x(t)cos(2\pi\nu t)dt - i \int_\mathbb R x(t)sin(2\pi\nu t)dt
\end{align}


\begin{align}
X(-\nu) &= \int_{\mathbb R}x(t) \cos (2\pi (-\nu)t )\: dt\\
&= \int_{\mathbb R} x(t) \underbrace{\cos(-2\pi\nu t)}_{\cos(2\pi \nu t)}dt = X(\nu)\\
\end{align}

:::info
La TF d'un signal reel et pair est reelle et paire.
:::

Si x est reel et impair $\rightarrow$ Sa TF est imaginaire pure et impaire


\begin{align}
X(\nu) &= -i\int_{\mathbb R} x(t) \sin (2\pi \nu t)dt\\
X(-\nu) &= -i \int_{\mathbb R} x(t) \sin(2 \pi (- \nu) t)dt \\
&= -i \int_{\mathbb R} x(t) \underbrace{\sin(-2 \pi  \nu t)}_{-sin(2 \pi \nu t)}dt \\
&= i \int_{\mathbb R} x(t) \sin(2\pi \nu t )dt = - X(u)
\end{align}


Dans le cas général:

\begin{align}
X(\nu) \in \mathbb{C},\;X(\nu) &= Re(X(\nu)) + i Im(X(\nu))\\
&= | X(\nu) | e^{i\phi(X(\nu))}
\end{align}
$|X(\nu)| \Rightarrow spectre \rightarrow$ am plitudes des frequences du sigal


:::info
$x=|Z|cos(\phi)$
$y=|Z|sin(\phi)$
$Z=x+iy = |Z|e^{i\phi(Z)}$
$Z = \sqrt{x^2 + y^2}$
$\phi(Z)=arctan(\frac{y}{x})$
:::

![](https://upload.wikimedia.org/wikipedia/commons/thumb/a/ab/Complex_number.svg/1200px-Complex_number.svg.png)

\begin{align}
x \overbrace{\rightarrow}^{\mathbb F} X\\
x(t -t_0) \overbrace\rightarrow^{\mathbb F}& \int_{\mathbb R} x\underbrace{(t -t_0)}_{u = t -t_0 | t = t_0 + u | dt = du} e^{-i 2 \pi \nu t} dt\\
&= \int_{\mathbb R} x(u) e^{-i 2 \pi \nu (t_o +u)}du\\
&= \int_{\mathbb R} x(u) e^{-i 2 \pi \nu u}  e^{-i 2 \pi \nu t_0} du
\end{align}

$\mathbb F(x(t-t_0))= e^{i2\pi\nu t} \underbrace{\int_\mathbb R x(u) e^{-i2\pi\nu t} du} _{X{\nu}}$

$\mathbb F(x(t-t_0)) = X(\nu) e^{-i2\pi\nu t_0}$
$|\mathbb F(x(t-t_0))| = |X(\nu) e^{-i2\pi\nu t_0}| = |X(\nu)|$
Le module n'as pas change

\begin{align}
\phi(\mathbb F(x(t-t_0))) &= \phi(X(\nu) e^{-i2\pi\nu t_0}) \\ &= \phi(X(\nu)) + \phi(e^{-i2\pi\nu t_0}) \\ &= \phi(X(\nu))-2\pi\nu t_0
\end{align}
La phase a change
$\Rightarrow$ position/localistaion des frequences dans le signal


:::warning
module $\rightarrow$ amplitude des frequences
phase $\rightarrow$ position des frequences
:::

$cos(2\pi \underbrace{f_0}_{frequence} t) \rightarrow^\mathbb F \frac{1}{2}(\delta(\nu -f_0) + \delta(\nu + f_0))$

$\sin(2\pi f_0 t) \rightarrow^\mathbb F \frac 1 2 (\delta (\nu + f_0) - \delta(\nu -f_0))$

la transformee de Fourrier d'une gaussienne est une gaussienne


$x_N = x_\infty * \Pi_N$
$\mathbb F(x_N) = \mathbb F(x_\infty * \pi_N)$
$\qquad \: \: \: \: = \mathbb F(x_\infty) * \mathbb (\Pi_N)$














--- 