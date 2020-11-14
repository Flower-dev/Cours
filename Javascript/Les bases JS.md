# Les bases du JavaScript

1 variable permet de garder en mémoire 1 valeur. Il faut la déclarer avec `var`

une variable peut changer de valeur &  de type au cours de l'exécution de l'algorithme. 

## Les types de variables : 

Les nombres exemples : 

```js
var a = 2
var b = 3.4 /*pour les nombres décimaux mettre des . et non des , */
var c = -45
var d = 1/3
```

Les chaines de caractère  exemples : 

```js
var a = "Bonjour à tous"
var b = 'Hello wolrd'
```

Les booléens permettant de stocker des infos qui sont soient vraies soient fausses 

```js
var vrai = true
var jeSuisFaux = false
```

La différence entre `var` & `let`

`let` permet de déclarer des variables dont la portée est limitée à celle du bloc dans lequel elles sont déclarées. Le mot-clé `var`, quant à lui, permet de définir une variable globale ou locale à une fonction (sans distinction des blocs utilisés dans la fonction).

Une autre différence entre `let` et `var` est la façon dont la variable est initialisée : pour `let`, la variable est initialisée à l'endroit où le parseur évalue son contenu.

## Les tableaux : 

Ils permettent de stocker une liste d'informations (peut importe le type de variable). Exemples : 

```js
var listeEleves = ['Marion', 'Alice', 'Martin', 'Maxime']
var demo = [true, 10, 'Alice']
```
 Il est possible de récupérer un élément dans un tableau en utilisant la notation [i] où i est un nombre représentant l'index de l'élément à récupérer (cet index commence par 0)

Exemple avec le tableau du dessus : 

```js
listeEleves[0] // Marion
listeEleves[3] //Maxime

demo[1] // 10
demo[20] // undefined
```

## Les objets 

Ils permettent de stocker des infos plus complexes qu'une simple liste. Exemple : 

```js
var eleve = {
   clef: 'valeur',
   nom: 'Jean',
   age: 18,
   notes: [10, 4, 18] 
}
```

Les "clefs" = des propriétés et pour récupérer les valeurs associées il faut faire : 

```js
eleve.nom // Jean
eleve.notes // [10, 4, 18]
eleve.notes[1] // 4
// On peut aussi utiliser une notation proche de celle des tableaux
eleve['notes'] // [10, 4, 18]
```

Les objets peuvent contenir des objets en valeur, exemple : 

```js
var eleve = {
    notes: {
        math: 18,
        francais: 14   
    }   
}
// Pour récupérer la note de math de l'élève on peut alors faire
eleve.notes.math // 18
eleves.nom // undefined
```

## Les conditions 

```js
if (<booleen>) {
    <code si vrai>
} else {
    <code si faux>
}
```

Les opérateurs de comparaison : 

```js
a == b // a égale à b
a === b // a == b et a est de même "type" que b
a >= b // a supérieur OU égal à b
a > b   // a strictement supérieur à b
a <= b // a inférieur OU égal à b
a < b   // a strictement inférieur à b
```


Il est possible d'utiliser les opérateurs booléens permettant de combiner plusieurs conditions ensembles : 

```js
// && ET
true && true // true
true && false // false
false && true // false
false && false // false

// || OU
true || true // true
true || false // true
false || true // true
false || false // false

// ! NON
!true # false
!false # true
```

Le ternaire ou opérateur conditionnel permet de raccourcir une condition en une seule ligne 

```js
// condition ? <expression si vrai> : <expression si faux>
age = 19
"Je suis " + (age >= 18 ? "majeur" : "mineur")
```

## Les conditions

Les boucles while permettent d'exécuter un code tant que la condition passée en paramètre n'est pas satisfaite, exemple : 

```js
var i = 0 
while (i < 3) {
    "Je compte " + i
    i = i + 1 // peut aussi s'écrire i++
}
```

Il est possible de sortir de la boucle grâce au mot clef `break` exemple : 

```js
var i = 0 
while (i < 3) {
    "Je compte " + i
    if (i == 1) {
        break
    }
    i++
}
```

La boucle for permet d'exécuter un code un certain nombre de fois en précisant manuellement l'intervalle pour lequel on souhaite faire la boucle, exemple : 

```js
var i = 0 
for (var i = 0; i < 3; i++) {
    "Je compte " + i
}
```

La boucle for est très utile pour parcourir un tableau, exemple : 

```js
var eleves = ['Marion', 'Martin', 'Alice']
for (var i = 0; i < eleves.length; i++) {
    eleve[i] // vaudra alternativement : Marion, Martin et Alice
}
```

## Les fonctions 

exemple de fonction : 

```js
function saluer (nom) {
    return "Salut " + nom
}
// On appel ensuite notre fonction avec 
saluer('Marc') // Salut Marc
```
ou 
```js
var saluer = function (nom) {
    return "Salut " + nom
}
```






