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

Voici un exemple de code CSS pour l'animer :

```scss
$cd-txt: #6300a0;
$cd-txt--invalid: #fff;
$cd-danger: #b20a37;
.form {
    &__group {
        & input {
            border: 2px solid $cd-box;
            border-radius: 100rem;
            color: $cd-txt;
            font-family: 'Montserrat', sans-serif;
            font-size: 2.5rem;
            outline: none;
            padding: .5rem 1.5rem;
            width: 100%;
            transition: background-color 500ms;
            &:focus {
                border: 2px solid $cd-txt;
            }
            &:not(:focus):invalid {
                background-color: $cd-danger;
                border: 2px solid $cd-danger;
                color: $cd-txt--invalid;
            }
        }
    }
}
```

Modifiez les éléments voisins avec les pseudoclasses
Les pseudoclasses sont parfaites pour déclencher des transitions sur l’élément auquel elles sont affectées, par exemple pour changer le style d’un bouton pour lequel l’état `:hover` est modifié, ou un champ dont l’état `:invalid`est activé. Mais vous pouvez également utiliser les pseudoclasses pour changer le style d’autres éléments.


Il est possible de combiner des pseudoclasses entre ellles pour créer des sélecteurs plus précis

:warning: le but est de créer des animations engageantes et naturelles et pour cela, il suffit de suivre les 12 principes de l'animation (fondateurs = les studios Disney)

- Squash and Stretch, pour compresser et étirer un élément ;
- Anticipation, pour préparer l’audience à un mouvement à venir ;  
- Staging (mise en scène), pour guider les yeux de l’utilisateur vers les éléments importants d’une page ;
- Straight Ahead and Pose to Pose (toute l'action d'un coup et partie par partie), qui correspond davantage à l'animation traditionnelle mais fait penser à la différence transitions/keyframes ;
- Follow Through and Overlapping Action (continuité du mouvement initial et chevauchement de deux mouvements consécutifs), pour faire accélérer et décélérer un élément en fonction de sa masse ;
- Slow in and slow out (ralentissement en début et en fin de mouvement), basé sur le fait que les objets ne démarrent pas et ne s’arrêtent pas instantanément ;
- Arc, pour créer des mouvements naturels ;
- Secondary Action (action secondaire), pour séparer différentes parties d’une scène dans une animation ;
- Timing, pour faire se déplacer les objets à une vitesse crédible ;
- Exaggeration (exagération), pour donner du caractère et de la personnalité à une animation ;
- Solid Drawing (notion de volume), pour que les animations correspondent au résultat souhaité ;
- Appeal (charisme), pour rendre les animations plus dynamiques.


Il est possible d’animer autant de propriétés que l’on veut avec les transitions ;
le mot clé   `all` permet d’appliquer des transitions simultanément à toutes les propriétés ;
ou bien on peut séparer les animations par des virgules, ce qui permet de leur donner des valeurs différentes. Exemple :  `transition: transform 450ms, background-color 300ms;`
on peut décaler le départ des transitions avec  `transition-delay` ;
la valeur de  `transition-delay`  peut également être définie directement dans la propriété  `transition`.


l’accélération et la décélération des transitions sont contrôlées par la propriété  `transition-timing-function`;
si aucune fonction de timing n’est indiquée, la transition utilisera la fonction `ease`. Elle suit un profil d’accélération plus net, et une rampe de décélération plus prononcée;
parmi les autres mots clés pour les fonctions de temporisation, on peut trouver `ease-in`,   `ease-out`,`ease-in-out`, et `linear`;
quand aucune fonction de timing par défaut ne correspond à l’animation, il est possible de créer ses propres courbes d’animation personnalisée à l’aide de la fonction `cubic-bezier()` ;
il existe des outils pour ajuster les effets de timing avec la fonction `cubic-bezier()`.


Les animations correspondent à des successions d'images -->  Frames Per Second (FPS)
Pour info : Les images par seconde, ou FPS, représentent le nombre d’images individuelles affichées en une seconde. Plus les FPS sont élevées, plus le mouvement paraît fluide.

**comment le navigateur passe des codes HTML et CSS à une page web ?**

Pour passer des codes CSS et HTML… à une page web, le navigateur passe par plusieurs étapes pour afficher une page. Voici les étapes qui nous intéressent pour le rendu de nos animations :

1- Style : le navigateur reçoit le code HTML. Il va l'interpréter pour comprendre la structure du DOM (Document Object Model). Ainsi, pour chaque balise HTML, il crée un élément du DOM, un peu comme un arbre de nœuds. Il parcourt ensuite le CSS, et détermine quelles règles s’appliquent à quels éléments. À partir de là, il va créer la structure qui s'affichera.

2- Layout (mise en page) : maintenant que le navigateur connaît les styles et les éléments à afficher, il détermine la taille des éléments et où les placer.

3- Paint (peinture) : le navigateur transforme les éléments en pixels en utilisant les styles de l’étape 1, et les positions et dimensions déduites de l’étape 2.

4- Composition : le navigateur combine tous les éléments pour composer la page qui s’affiche dans le navigateur.
