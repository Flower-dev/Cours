# COURS LES PREPROCESSEURS CSS : UTILISATION DE SASS

## PARTIE 1:
Le but de ce cours est de rendre le code CSS plus propre

Les variables permettent de changer 1 seule valeur à 1 seul endroit --> répercution sur la suite du code
Il faut aussi faire un code imbriqué

Les boucles automatisent les tâches répétitives

MOTS IMPORTANTS :
- DRY = Don't Repeat Yourself
- BEM = Bloc Element Modificateur
- NESTING = Structurer le code en le hiérarchisant
- IDE = Intergrated Development Environment (équivaut à un traitement de texte)

La compilation = 1 processus permettant de transformer le SASS ou du moins le `.scss` en `.css` pour se faire, il faut taper la commande suivante dans son terminal : ```sass scss/index.scss css/index.css``

Pour écrire du SASS il existe deux extensions de fichier le `.sass` et le `.scss` (ce dernier est beaucoup plus utilisé)

Les combinateurs (regrouper et combiner des sélecteurs CSS), il en existe plusieurs types :
- parent
- descendant
- parent > enfant
- adjacent

:warning:**ATTENTION** : un élément enfant a un lien direct et immédiat avec son élément parent ce qui n'est pas le cas des éléments descendants

Concaténer = relier et pour cela il faut utiliser le symbole & (esperluette)
à utiliser pour `:focus` ou `:hover`

Ne pas abuser du nesting car ce dernier augmente la spécificité, il faut donc regrouper des sélecteurs pertinents

Utilisation de BEM avec SASS : combiner les sélecteurs BEM avec les nesting SASS --> il faut nester dans SASS sans aller au delà des principes de BEM en utilisant & (esperluette)
ex : `.block_element` deviendra : `&_element`
     `.block_element--modification` deviendra : `&--modification`
:warning:**ATTENTION** : il n'y a pas de `.` devant `&`

Utiliser des spécificités là où c'est nécessaire permet de créer un système de sélecteurs propre et maintenable + stable et prévisible MAIS faire attention aux incohérences de spécificité --> création de bugs:warning:

Pour nommer un modificateur il faut écrire :
`.block--modification{}`

Le sélecteur `.id` a une plus grande spécificité que le sélecteur `.class`

Q : Dans SASS, sous quelle forme se compile le symbole `&` ?
R : Le parent du sélecteur dans la hiérarchie

## PARTIE 2:

Petit rappel : les variables permettent de rendre le code plus lisible et éviter les erreurs
Pour déclarer une variable, il faut utiliser le symbole `$` ex : `$color-primary`
Les variables sont utilisées pour :
- les couleurs
- les chaines de caractères (strings)
- les nombres
- les listes et maps

les variables ne stockent que des valeurs et c'est tout

Les mixins permettent de stocker des blocs entiers de code (pour les nommer faire référence à leur role ou fonction)
ex : `@mixin heading-shadow` et pour la nommer dans le code par la suite faire `@include heading-shadow`

Il est possible d'ajouter un argument à une mixin comme `@mixin heading-shadow ($color)`

Les extensions sont presque identiques aux mixins et évitent les répétitions dans le code compilé mais privilégier les mixins

Pour utiliser les extensions faire : `._____________{}` puis l'appeler avec `@extend .________________________;`

`@exend` duplique les sélecteurs et non les règles ce qui permet d'avoir un CSS plus clair et moins lourd

:warning:**ATTENTION** : les sélecteurs non utilisés augmentent la taille du fichier CSS & ajoute de la confusion MAIS plutôt que de mettre un `.` pour les extensions mieux vaut privilégier le symbole `%`qui permet à SASS de créer un placeholder (classe silencieuse). Il faut donc écrire : `%______________{}` et l'appeler par la suite `@extend %_________________________;`

Les extensions permettent de ne pas réécrire plusieurs fois de très nombreuses lignes de code répétitives
PRIVILEGIER LES PLACEHOLDER DE REGLES

Comment choisir entre les mixins et les extensions qui sont quand même très semblables ??
les mixins tolèrent les arguments mais créent du code répétitif en `.css` (à privilégier au maximum)
les extensions ne tolèrent pas les arguments mais génèrent des sélecteurs dupliqués

Apprendre à utiliser les fonctions :
Pour commencer, les fonctions sont des bouts de code préfabriqués

Il est possible d'écrire les couleurs en valeur héxadécimale mais dans SASS, il est possible de les exprimer en `hls(...)` ou Hue Saturation Lightness (teinte saturation clarté)
pour rendre une couleur plus foncée, il faut utiliser la fonction `darken(...)`

Les conditions permettent de rendre l'interface du site plus vivante car pour le moment le code n'est pas dynamique du tout

la condition : la condition de la couleur est inférieure à 25%
IF (vrai) Eclaircir la couleur
ELSE (faux) Assombrir la couleur

En code cela donne :

```scss
@if(lightness($color)<25%){
  $color:lighten($color, 10%);
}
@else{
  $color:darken($color,10%)
}
```

## PARTIE 3:

Comment faire pour se repérer dans son code avec toutes ces variables, mixins, ... qui se trouve en haut du codebase et éviter de scroler de haut en bas ??

Pour ordonner tous ces nouveaux fichiers, il faut utiliser ce qui s’appelle le système de fichiers 7-1. Le “7”, ce sont les sept directories thématiques (des dossiers, en langage de développeur) pour ranger les fichiers, qui sont regroupés dans le “1” : un fichier .scss unique se compilant sous forme de feuilles de style CSS pour votre site :

- Base.
- Utils.
- Layout (mise en page).
- Composants.
- Pages.
- Themes.
- Vendors (tiers).

Savoir faire la différences entre les variables, les mixins, les listes et les maps !!

les *variables* permettent de stocker une valeur

les *mixins* et les extensions permettent de stocker un groupe de propriétés
--> mieux vaut privilégier les mixins aux extensions

Les *listes* permettent de regrouper plusieurs valeurs dans une variable c'est le cas par exemple pour les paddings que l'on peut écrire de cette manière :
```scss
$padding-dimensions: 1rem 2rem 3rem 4rem;
```

Les *maps* sont assez semblables aux listes mais elles assignent à chaque valeur un nom sous forme d’une paire clé/valeur :
```scss
$font-size: (logo:7rem, heading:5rem, project-heading:4rem, label:2rem);
```

En assignant chaque valeur à une clé, ou un nom,  c’est beaucoup plus simple de se souvenir et de comprendre son utilité.

Les règles sont beaucoup plus strictes pour écrire des maps que pour les listes. Avec les listes, à peu près tout est optionnel (les parenthèses, les virgules...).

Mais le contenu des maps doit être entouré d’une paire de parenthèses et doit utiliser des virgules pour séparer les paires clé/valeur
```scss
$map: (
  key-01: value-01,
  key-02: value-02,
  key-03: value-03
);
```

Pour accéder à la valeur d’une map, c’est aussi un peu différent. Avec les maps, il faut utiliser la fonction `map-get()`, celle-ci nécessite deux arguments : le premier est le nom de la map (ici `$font-size`), et le second est le nom de la clé (ici label).

```scss
$font-size: (logo:7rem, heading:5rem, project-heading:4rem, label:2rem);
.form{
  &__field {
    & label {
        font-size: map-get($font-size, label);
      }
  }
}
```

- Les listes et les maps sont des collections de valeurs.
- Les listes ont une syntaxe très flexible ; on peut utiliser ou non des virgules, ou rien. Pareil pour les parenthèses.
- On accède aux valeurs d’une liste en appelant leur index via la fonction `nth()` --> `nth($list, index)`.
- En Sass, les indexs des listes commencent à 1.
- Les maps sont semblables aux listes, sauf que chaque valeur reçoit un nom qu’on appelle une clé :  `$map(key: value)`.
- On accède aux valeurs d’une map via la fonction `map-get()` --> map-get($map, key).
- Les maps et les listes peuvent contenir n’importe quel type de données Sass, y compris d’autres listes et maps.


Apprendre à utiliser les boucles !!

Les boucles sont des structures permettant d’exécuter un certain nombre de fois une série d’instructions. C'est donc la répétition d'un ensemble d'action.
En appliquant une boucle au sein d'une mixin de texte, Sass peut automatiquement créer les bons sélecteurs et les bons ensembles de règles pour chaque élément de la map soumise.

La boucle la plus utilisée dans SASS est la boucle `@each` et c'est aussi la plus simple à mettre en place. Quand on écrit une boucle `@each` dans SASS, il faut indiquer pour chaque paire clé/valeur d'une `$map` qu'il faut effectuer une tâche en l'écrivant de cette manière :

```scss
@each $key, $value in $map {
}
```

SASS va aller dans `$map`et créer des variables temporaires pour `$key`et `$value`et ce, pour chaque ensemble clé/valeur qu'il trouve (ces variables temporaires sont invisibles pour le reste du code)

La syntaxe d'interpolation `(#{variable})` ou autrement appelée substitution de variable, permet d’utiliser la valeur d’une variable au sein d’une chaîne de caractères (ou string) et de la remplacer par une autre.
En `.scss`cela donne :

```scss
@mixin txt-input-palette($palettes) {
  @each $state, $palette in $palettes{
      &:#{$state}{
        border: .1rem solid map-get($palette, border);
        background-color: map-get($palette, bg);
        color: map-get($palette, txt);
      }
  }
}
```

Dans cet exemple a été utilisé l'esperluette `&`suivie de `:` qui ont été attribués à `$state`


Ne surtout pas oublier de faire une mise en page responsive afin que le site s'adapte à tous les types d'écrans (mobile, tablette, ordi ...)
Pour que la mise en page d'un site s'adapte à n'importe quel type de support, il faut mettre en place des **media queries** qui permettent d'indiquer au navigateur d'utiliser un ensemble de règles alternatif (sous certaines conditions)
Pour exécuter une media query, il faut utiliser la règle CSS `@media`suivie d'un argument et d'accolades comme par exemple :

```scss
@media(max-width:599px){
  }
```

Les resolutions indiquées pour les media queries = des breakpoints (limites liées à la résolution de l'écran)

La syntaxe CSS standard pour les media queries consiste à placer un sélecteur et son ensemble de règles directement entre les accolades de la query. Lorsque la résolution de l’écran correspond au breakpoint, alors le breakpoint prendra le pas sur l’ensemble de règles par défaut :

```scss
@media (max-width: 599px) {
  .proj-grid {
      grid-template-columns: 1fr;
  }
}
```

Le terme mobile-friendy = adpaté sur mobile

Avec SASS, il est possible de placer les media queries directement dans les sélecteurs :

```scss
.proj-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  @media (max-width: 599px) {
      grid-template-columns: 1fr;
  }
}
```

Quand Sass compile les media queries, il vérifie dans quel sélecteur elles sont imbriquées et affiche une media query standard avec le sélecteur nesté dedans :

```scss
.proj-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
}
@media (max-width: 599px) {
.proj-grid {
  grid-template-columns: 1fr;
}
}
```

Apprendre à utiliser les breakpoints
Il faut commencer par créer une map `$breakpoints`afin d'y stocker les différents breakpoints
exemple :

```scss
$breakpoints: (
  mobile: 599px
);
```

Utiliser également les mixins pour éviter les répétitions et obtenir quelque chose de plus sémantique :

```scss
@mixin mobile-only {
  @media screen and (max-width: map-get($breakpoints, mobile)){
      grid-template-columns: 1fr;
  }
}
```

Le bout de code ci-dessus possède des règles qui ne s'appliquent qu'aux résolutions mobile car on a : `@mixin mobile-only`

Si on rattache ce bout de code à `bloc.proj-prev`, cela donne :

```scss
@mixin mobile-only {
  @media screen and (max-width: map-get($breakpoints, mobile)){
      grid-template-columns: 1fr;
  }
}
.proj-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  @include mobile-only;
}
```


Utiliser la directive `@content`
exemple :

```scss
@mixin mobile-only {
  @media screen and (max-width: map-get($breakpoints, mobile)){
      @content;
  }
}
```

Quand Sass compile les instances de la mixin, il remplacera `@content`placé par le code que vous aurez placé à l’intérieur de l’instance de la mixin.

Q: *Comment on s’y prend, au juste, pour ajouter du contenu dans une instance de mixin ?*

R:

```scss
@mixin mobile-only {
  @media screen and (max-width: map-get($breakpoints, mobile)){
      @content;
  }
}
.proj-grid {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  @include mobile-only{
      grid-template-columns: 1fr;
  }
}
```

Dans cet exemple, SASS remplacera `@content`par `grid-template-columns: 1fr` lorsqu'il compilera le code

```scss
.proj-grid {
display: grid;
grid-template-columns: repeat(3, 1fr);
}
@media screen and (max-width: 599px) {
.proj-grid {
  grid-template-columns: 1fr;
}
}
```

`@content`est donc un placeholder qui sera remplacé au moment de la compilation, instance par instance.
