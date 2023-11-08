# BEM (_Block Element Modifier_)

C'est une **méthode de nommage** des sélecteurs CSS.  
Elle se base sur les classes :
tous les éléments à styliser sont ciblés par un nom de classe.

→ avantage : évite le problème des spécificités

> tous nos éléments auront la même spécificité (0,1,0)

Syntaxe :

```css
.block__element--modifier
```

On va regrouper nos éléments par **blocks** : une entité autonome
qui a un sens en soi.

Exemple : `<div class="actors">`

À l'intérieur des blocs, on retrouve généralement des enfants,
appelés **elements**.
Attention si un enfant a une signification en soi,
il devient (ou peut devenir) un block…

Exemple : `<ul class="actors__list">`

> ça permet de devoir cibler notre élément en CSS avec
> quelque chose du genre `.actors ul`

Pour signifier un changement d'état, on utilise un **modifier**

Exemple : `<li class="actors__item actors__item--is-active">`

> Les **modifier** sont très utilisés pour les button notamment
>
> ```css
> .button {
>   border: 0;
>   border-radius: 4px;
>   padding: 1rem;
>   background-color: #ddd;
>   color: #666;
> }
>
> .button--success {
>   background-color: #138808;
>   color: #fff;
> }
>
> .button--danger {
>   background-color: #cc0;
>   color: #fff;
> }
>
> .button--full-width {
>   width: 100%;
> }
> ```
>
> ```html
> <button class="button">Bouton par défaut</button>
> <button class="button button--success">Bouton Succès</button>
> <button class="button button--danger">Bouton Erreur</button>
> <button class="button button--danger button--full-width">Bouton Erreur + Large</button>
> ```
