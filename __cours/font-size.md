# Taille des polices

Pour jouer sur la taille des polices, nous utilisons `font-size` qui accepte
une valeur en pixels… Mais pas seulement, à vrai dire, il est même vivement
conseillé d'utiliser autre chose que les pixels !

On va utiliser le **cadratin**, _em_ en anglais (`em` est d'ailleurs le symbole de l'unité).
L'em est une **unité relative** : 1 em va correspondre à la taille de la police
de l'élément parent (pour le `font-size`) ou à la taille de la police de
l'élément courant pour les autres propriétés (`width`, `padding`).

Ainsi, par défaut, la taille de la police des navigateurs est 16 px, on aura
donc :

```css
html,
body,
main {
  font-size: 1em; /* 16px */
}

h1 {
  font-size: 2em; /* 32px = 2 * 16px */
}

p {
  font-size: 0.8125em; /* 13px = 0.8215 * 16px */
}

p strong {
  /*
    ici la taille relative sera donc calculée par rapport au parent (p)
  */
  font-size: 1.23em; /* 16px = 1.23 * 13px */
  /* ici le parent (`p`) a une taille de 13 px, 1 em égal donc 13 px */
}

div {
  font-size: 0.8125em; /* 13px = 0.8215 * 16px */
  padding: 2em; /* 26px = 2 * 13px */
  /* pour les propriétés autres que `font-size`, la valeur de référence
  est la taille de la police de l'élément lui-même, ici 13 px */
}
```

Exercice :

Considérant le code suivant (voir [em.html](./em.html))

```html
<html>
<head>
  <style>
    * { font-size: 2em; }
  </style>
</head>
<body>
  <main>
    <section>
      <p>Quelle sera la taille de la police dans cette <span>span</span> ?</p>
    </section>
  </main>
</body>
</html>
```

→ Réponse : 1024px !
> `html = 2em = 2 * 16px = 32px`
> `body = 2em = 2 * html = 2 * 32 = 64px`
> `main = 2em = 2 * body = 2 * 64 = 128px`
> `section = 2em = 2 * main = 2 * 128 = 256px`
> `p = 2em = 2 * section = 2 * 256 = 512px`
> `span = 2em = 2 * p = 2 * 512 = 1024px`

Donc attention, l'utilisation des `em` peut être périlleuse…
Pour plus de faciliter, on va utiliser les `rem` (_root em_), c'est le même
principe que les `em` mais on se base toujours sur la « racine »,
_i.e._ la balise `<html>`.

> Note, en utilisant `* { font-size: 2em; }`, on lui dit que `<html>`
> fait deux fois sa taille (donc 32 px), puis tous les autres éléments
> font 2 fois la taille de `<html>`, donc 64 px. (voir [rem.html](./rem.html))
>
> On utilisera, bien entendu, jamais le sélecteur universel `*` pour
> déclarer nos `font-size` mais des sélecteurs plus précis.

Qu'on utilise les `em` et/ou les `rem`, ça peut être un peu embêtant de
devoir convertir la taille des polices en pixels vers les `rem` car la
taille par défaut est 16 px…
Je préfère la base-10 personnellement ! Et bien faisons ça :

```css
html { font-size: 10px; } /* BAD IDEA */
/* De nombreuses personnes avec une déficience visuelle vont vouloir
modifier les 16 px par défaut en mettant 24 px par exemple…
si on fait ça, notre site les obligera à utiliser notre base 10 */
html { font-size: 62.5%; } /* GOOD! */
/* Par défaut, on aura 10 px au lieu de 16 (10 / 16 = 0.625) ; 
et on prend en compte la modification de cette valeur par défaut…
Ainsi je personnalise une valeur par défaut de 24 px, la taille de référence
du site sera 24 * 62.5 % = 15px */
```

Par la suite, pour calculer une taille, on se basera sur la base-10 :

| Taille désirée en pixels | Taille à renseigner en rem |
|--------------------------|----------------------------|
| 10                       | 1rem                       |
| 16                       | 1.6rem                     |
| 24                       | 2.4rem                     |
| 8                        | .8rem                      |

> [Article](https://www.aleksandrhovhannisyan.com/blog/62-5-percent-font-size-trick/)
