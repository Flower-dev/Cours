## COURS : FLEXBOX

Lorsque l'on travaille avec des boîtes flexibles deux axes i interviennent :
- l'axe principal (main axis)
- l'axe secondaire (cross axis)

L'axe principal = définit par la propriété `flex-directory`
L'axe secondaire = l'axe qui est perpendiculaire à l'axe principal

Du côté de l'axe principal :
la propriété `flex-direction` peut prendre différentes valeurs comme :
- `row`
- `row-reverse`

Dans ces deux cas, l'axe principal sera aligné avec la direction en "ligne"

- `column`
- `column-reverse`

Dans ces deux cas, l'axe principal suivra la direction de bloc et progressera le long de l'axe perpendiculaire au sens d'écriture.

Du côté de l'axe secondaire :

L'axe secondaire =  perpendiculaire à l'axe principal. Donc si `flex-direction` prend la valeur `row` ou `row-reverse`, l'axe secondaire suivra l'axe des colonnes. 

Si l'axe principal est `column`ou `column-reverse`, l'axe secondaire suivra celui des lignes.

La zone d'un document sujette au modèle de disposition flexbox est appelée un conteneur flexible.
Pour créer un conteneur flexible, il faut utiliser la propriété `display` suivie de `flex` ou `flex-inline`

La propriété `flex-wrap`permet de faire un retour à la ligne mais si on utilise `nowrap`les éléments seront rétrécis pour tenir sur la même ligne

La propriété `flex-basis`définit la taille de l'élément en termes d'espace occupé. La propriété `flex-grow`est un entier positif qui, lorsqu'elle est définie, permet aux éléments flexibles de s'étendre à partir de la mesure de `flex-basis`. La propriété `flex-grow` permet de gérer la façon dont l'espace est ajouté sur l'axe principal. La propriété `flex-shrink` permet quant à elle de contrôler la façon dont l'espace est réduit. S'il n'y a pas suffisamment d'espace dans le conteneur pour disposer les éléments et que `flex-shrink` est un entier positif, l'élément peut alors devenir plus petit que la taille définie par `flex-basis`.

La propriété align-items permet d'aligner les éléments le long de l'axe secondaire.

On peut également utiliser les propriétés suivantes :
- `stretch`
- `flex-start`
- `flex-end`
- `center`

La propriété `justify-content` est utilisée afin d'aligner les éléments le long de l'axe principal dans la direction définie par `flex-direction`

`space-between` afin de répartir l'espace disponible de façon égale entre chaque élément
