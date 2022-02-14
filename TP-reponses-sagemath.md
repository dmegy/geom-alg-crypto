TP
===

Exercice 1
---

(Nombre de points de la courbe $y^2=x^3-x$.)

Première question : le nombre de points :
```
E = EllipticCurve(GF(9),[-1,0])
E.cardinality()
> 16
```
Il y a donc seize points. Si on devait faire ça à la main, on calculerait le nombre de points sur $\mathbb F_3$, puis la fonction zêta, et on en déduirait le nombre de points sur $\mathbb F_{3^k}$.
Ceci ne donne pas la structure de groupe. On peut demander à Sage :
```
E.abelian_group()
> Additive abelian group isomorphic to Z/4 + Z/4 embedded in Abelian group of points on Elliptic Curve defined by y^2 = x^3 + 2*x over Finite Field in z2 of size 3^2
```
Le groupe n'est donc pas cyclique.

Remarque : la courbe est maximale pour la borne de Hasse.





Exercice 2
---


```
E = EllipticCurve(GF(11),[1,3])
E.cardinality()
> 18
```
Le groupe est donc cyclique. On peut demander un générateur à Sage :
```
E.gens()
> ((5 : 1 : 1),)
```
On vérifie :
```
P=E(5,1)
P.order()
> 18
18*P
> (0 : 1 : 0)
2*P
> (4 : 4 : 1)
9*P
>(3 : 0 : 1)
```
Note : le point de coordonnées affines $(4,4)$ est d'ordre $9$. Comme on sait que le point $(3,0)$ est d'ordre deux, on peut prendre la somme des deux points pour avoir un point d'ordre $18$ :
```
Q=E(3,0)+E(4,4)
Q.order()
```

Exercice 3
---
On considère, sur $\mathbb F_{101}$, la courbe elliptique $y^2=x^3+7x+1$. Calculer l'ordre du point $(0,1)$ et en déduire $|E(\mathbb F_{101})|$.
```
E = EllipticCurve(GF(101),[7,1])
P=E(0,1)
P.order()
> 116
```
Comme l'ordre de ce point est 116 et que l'intervalle de Hasse de la courbe est [82,122], on en déduit que la courbe possède exactement 116 points.

Exercice 4
---

On considère, sur $\mathbb F_{557}$, la courbe elliptique $y^2=x^3-10x+21$. Calculer l'ordre du point $(2,3)$ et en déduire $|E(\mathbb F_{557})|$.
```
E = EllipticCurve(GF(557),[-10,21])
P=E(2,3)
P.order()
> 189
```
L'ordre est $189$ et il n'y a qu'un seul multiple de ce nombre dans l'intervalle de Hasse de la courbe, à savoir $567$. La courbe possède donc exactement $567$ points.


