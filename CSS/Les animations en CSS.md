## LES ANIMATIONS EN CSS

# PARTIE 1 :

Il existe 2 moyens de créer des animations en CSS : **les transitions** et **les keyframes**

Les keyframes permettent de créer des animations plus élaborées mais elles sont assez complexes à mettre en place.

Les animations sont plus limitées mais plus simples à réaliser. Elles permettent à 1 élément de passer de l'état A à l'état B. Pour créer une transition, il est nécessaire de connaitre différentes informations :
- une propriété CSS à modifier ;
- une valeur initiale pour votre propriété CSS ;
- une valeur finale pour cette même propriété ;
- une durée ;
- un événement pour déclencher votre transition.

S'il on souhaite modifier un bouton pour que ce dernier grossisse au passage de la souris, il faut utiliser la propriété `transform`et la fonction `scale()`.

Voici le code HTML utilisé pour créer le bouton :

```HTML
<body>
    <div class="container">
        <div class="btn">
            Vois comme je grandis !
        </div>
    </div>
</body>
```

Le code SCSS qui lui est lié est :

```scss
$cd-btn: #011c37;
$cd-txt: #15DEA5;
.btn {
    background: $cd-btn;
    color: $cd-txt;
    font-size: 3rem;
    cursor: pointer;
    padding: 1.85rem 3rem;
}
```
Pour passer de l'état A à l'état B il faut donc utiliser la propriété `transform`et la fonction qui lui est associée `scale()` cela est à appliquer sur la classe `.btn`

```scss
$cd-btn: #011c37;
$cd-txt: #15DEA5;
.btn {
    background: $cd-btn;
    color: $cd-txt;
    font-size: 3rem;
    cursor: pointer;
    padding: 1.85rem 3rem;
    border-radius: 10rem;
    transform: scale(1);
}
```

Pour le moment, le bouton est fixe car il faut indiquer la valeur finale !
Pour que le bouton grossisse de 15% au survol de la souris, il faut utiliser la pseudoclasse `:hover`avec la fonction `scale()` définie sur 1.15

Niveau code cela donne donc :

```scss
$cd-btn: #011c37;
$cd-txt: #15DEA5;
.btn {
    background: $cd-btn;
    color: $cd-txt;
    font-size: 3rem;
    cursor: pointer;
    padding: 1.85rem 3rem;
    border-radius: 10rem;
    transform: scale(1);
    &:hover {
        transform: scale(1.15);
    }
}
```

:warning: Les transitions doivent être déclenchées par 1 changement d'état comme par exemple avec la pseudoclasse `:hover`.

Pour le moment, il n'y a aucune fluidité ... pour indiquer au navigateur  que le changement d’échelle, entre l’état inactif et le `:hover`, devra se faire via une transition animée, il faut utiliser la propriété `transition-property`au selecteur `.btn`. Cela permet d'indiquer que la propriété `transform`= celle sur laquelle il faut appliquer une transition

Niveau code cela donne donc :

```scss
$cd-btn: #011c37;
$cd-txt: #15DEA5;
.btn {
    background: $cd-btn;
    color: $cd-txt;
    font-size: 3rem;
    cursor: pointer;
    padding: 1.85rem 3rem;
    border-radius: 10rem;
    transform: scale(1);
    transition-property: transform;
    &:hover {
        transform: scale(1.15);
    }
}
```

La propriété `transition-duration` permet d'indiquer la durée que prendra la transition. Il est possible d'indiquer les durées en secondes (s) ou en millisecondes (ms)

Retour au code :

```scss
$cd-btn: #011c37;
$cd-txt: #15DEA5;
.btn {
    background: $cd-btn;
    color: $cd-txt;
    font-size: 3rem;
    cursor: pointer;
    padding: 1.85rem 3rem;
    border-radius: 10rem;
    transform: scale(1);
    transition-property: transform;
    transition-duration: 400ms;
    &:hover {
        transform: scale(1.15);
    }
}
```
Il est possible remplacer la propriété `transition-property`par la propriété `transition`qui permet de combiner toutes les propriétés en 1. Il faut commencer par le nom de la propriété laisser 1 espace puis indiquer la durée

```scss
transition: transform 400ms;
```

Si l'on reprend le code de tout à l'heure et que l'on fait les modifications nécessaires, cela donne :

```scss
$cd-btn: #011c37;
$cd-txt: #15DEA5;
.btn {
    background: $cd-btn;
    color: $cd-txt;
    font-size: 3rem;
    cursor: pointer;
    padding: 1.85rem 3rem;
    border-radius: 10rem;
    transform: scale(1);
    transition: transform 400ms;
    &:hover {
        transform: scale(1.15);
    }
}
```

Point sur les pseudoclasses :

Pour commencer il existe plus de 50 pseudoclasses dont `:hover`. Les pseudoclasses peuvent s'apparenter à 1 if/else en CSS.

Le survol de l’élément par la souris déclenche un changement d’état, de “non survolé” à “survolé". C’est bien ce changement d’état qui rend cette pseudoclasse parfaite pour nos animations. Pour déclencher une transition, il faut utiliser une pseudoclasse dont on sait que l’état changera selon l’interaction de l’utilisateur.

Quelques pseudoclasses à connaitre :

- `:hover` qui se déclenche au survole d'une souris
- `:active`qui s'active au clic de l'utilisateur
- `:focus` qui se déclenche lorsque son élément reçoit le focus (soit il est sélectionné à l'aide du clavier, soit il est activé avec la souris)
- `:valid`dont la validation du contenu s'effectue correctement par rapport au type de donnée attendu
- `:invalid` qui inversement, correspond à un élément dont la validation du contenu ne s'effectue pas correctement par rapport au type de donnée attendu
- `:not()` qui correspond à la négation. Elle prend un sélecteur en argument et permet de cibler les éléments qui ne sont pas représentés par cet argument
- `:checked` qui correspond aux input de type checkbox, option ou radio qui sont cochés
- `enabled`= un élément avec lequel il est possible d'interagir
- `disabled` correspond à un élément dont l'interaction a été bloquée



Comment réaliser un formulaire ??

En HTML cela donne :

```html
<body>
    <div class="container">
        <div class="form">
            <div class="form__group">
                <label for="">email</label>
                <input type="email" name="" id="">
            </div>
        </div>
    </div>
</body>
```
