TD5 - Révisions
===

Ce fichier markdown contient quelques lignes de code qui peuvent aider à vérifier les résultats obtenus à  la main.

Exercice 1
---
Pour vérifier si une courbe projective a ou n'a pas de points :

```
k=GF(2)
P.<x,y,z> = ProjectiveSpace(k, 2)
C = Curve(x^3+y^3+z^3+x^2*y+y^2*z+z^2*x+x*y*z, P)
C.closed_points()
```

(Pas de points sur $\F_{2}$!)

Exercice 3
---

Pour vérifier si la courbe $y^2=x(x-1)(x-2)(x-3)$ a des points singuliers:

```
k=GF(5)
P.<x,y,z> = ProjectiveSpace(k, 2)
C = Curve(y^2*z^2-x*(x-z)*(x-2*z)*(x-3*z), P)
C.singular_closed_points()
```

(Ici le point à l'infini est singulier : lorsqu'on donne une courbe hyperelliptique par sa forme affine, il est donc sous-entendu qu'on désingularise le point à l'infini.)


Exercice 7
---

Sur la courbe $y^2=x^3-x+1$ sur le corps à 11 éléments :

Nombre de points et structure du groupe abélien :
```
E = EllipticCurve(GF(11),[-1,1])
E.abelian_group()
> Additive abelian group isomorphic to Z/10 embedded in Abelian group of points on Elliptic Curve defined by y^2 = x^3 + 10*x + 1 over Finite Field of size 11
```
Fonction zêta :
```
E.zeta_function()
> (11*x^2 - 2*x + 1)/(11*x^2 - 12*x + 1)
```
On peut alors calculer le nombre de points sur $\mathbb F_{11^k}$ en calculant les racines complexes du numérateur. Pour $k=3$ la calcul à la main donne $11^3+1-2(1-30) = 1390$. Pour la structure de groupe, on commence par factoriser. Avec Sage : 
```
factor(1390)
> 2 * 5 * 139
```
Bref le groupe est cyclique. Vérification avec la machine: 
```
E = EllipticCurve(GF(11**3),[-1,1])
E.abelian_group()
> Additive abelian group isomorphic to Z/1390 embedded in Abelian group of points on Elliptic Curve defined by y^2 = x^3 + 10*x + 1 over Finite Field in z3 of size 11^3
```

Exercice 8
---
Question 2, pour $q=4$ : 
```
E = EllipticCurve(GF(4),[0,0,1,0,1])
E.abelian_group()
>Additive abelian group isomorphic to Z/3 + Z/3 embedded in Abelian group of points on Elliptic Curve defined by y^2 + y = x^3 + 1 over Finite Field in z2 of size 2^2
```
