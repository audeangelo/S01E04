# Positions

[MDN](https://developer.mozilla.org/fr/docs/Web/CSS/position)

En CSS, nous avons 5 positions possibles

## Static

Position par défaut, comportement standard : les _block_ sont en bloc,
les _inline_ sont alignés…

## Relative

L'élément occupe son espace, on dit qu'il est **dans le flux normal du document**,
il affecte alors le positionnement de ses voisins.

Comme en `static`… sauf qu'on peut le décaler grâce aux propriétés
`top`, `right`, `bottom`, `left` par rapport à son coin haut gauche.  
On dit qu'il est **positionné**.

> le décalage n'affecte pas la position des autres éléments

[Exemple](./positions.html)

> on peut jouer sur le chevauchement et qui vient au dessus grâce à la
> propriété `z-index` (le plus haut chiffre est dessus)

## Absolute

L'élément est **positionné** (affecté par `top`, `right`, `bottom`, `left`)
mais n'occupe plus son espace : il est **retiré du flux** normal.

Il est positionné par rapport à son plus proche **parent positionné** ou
au `body` (à la partie visible, sur l'écran, du `body`) (si aucun parent n'est positionné).

> le plus souvent, on positionne un de ses parents en `relative`

Attention, la largeur de l'élément n'est plus 100 % de son parent mais
prend la taille de son contenu (à moins de lui spécifier une taille).

Un élément `absolute` peut avoir des marges, mais elles ne fusionnent pas
avec les autres marges.

## Fixed

Caractéristiques identiques à absolute sauf qu'il est
**positionné par rapport au _viewport_**.  

Donc si le `body` est plus grand que le _viewport_, l'élément sera
fixé à sa position au _scroll_ de la page  
→ tester avec `body { height: 200vh; }`

## Sticky

La position de la boîte est calculée à partir du flux normal ;
l'élément se déplace dans son parent (ou son plus proche ancêtre de
défilement)) jusqu'à ce que le seuil donné par ses propriétés
`top`, `right`, `bottom`, `left` ne soit plus respecter.
Il va alors « se coller » à cette position.

> Petite « nouveauté » 2021 :
> au lieu de faire `top: 0; left: 0; right: 0; bottom: 0;`  
> on peur utiliser `inset: 0;`