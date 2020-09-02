# LES BASES DU JAVASCRIPT

:warning: version de JavaScript utilisée : ES6

## Qu'est ce qu'une variable ?

Les variables permettent d'enregistrer & de manipuler des données. Il est possible de comparer une variable à un contenant.

Une donnée placée dans une variable = 1 **valeur**.

:warning: Il est important de donner un **nom** à une variable afin de savoir ce qu'il y a dedans !

Voici quelques règles générales pour la création d'un nom :

- Utiliser des noms descriptifs dans l'ensemble du code.

- Eviter d'utiliser des abréviations ou de raccourcir les mots `annualRevenue` sera mieux que  `annualRev`

- Suivre une convention de nommage constante comme par exemple **camel case**. Dans cette convention, les noms sont constitués de plusieurs mots dont l'initiale est en capitale. Exemples : `numberOfCats`, `finalAnswer`,  `howLongCanThisVariableNameGet`, etc.

Pour créer une variable, il faut commencer par la déclarer en utilisant le mot clef *let* suivi du nom de la variable.

Voici un exemple de code :

Si l'on souhaite créer la variable Nombre de chat il suffit de faire :

```js
let numberOfCats = 2;
```

Il est possible de faire la même chose avec la variable Nombre de chiens ce qui donne :

```js
let numberOfDogs = 4;
```

Dans les deux lignes de codes ci-dessus, la convention de nommage utilisée =  **camel case**.

### Comment modifier la valeur d'une variable ?

La manière la plus simple = la réaffecter, exemple :

```js
let numberOfCats = 2;

numberOfCats = 4;
```
en faisant cela on ne peut pas faire grand-chose ... Il faut donc utiliser des **opérateurs**

Les opérateurs arithmétiques permettent de faire des opérations mathématiques de bases (addition, soustraction, multiplication & division)

**LES ADDITIONS & SOUSTRACTIONS**

Pour ajouter deux variables entre elles, il faut utiliser le signe `+`

```js
let totalCDs = 67;

let totalVinyls = 34;

let totalMusic = totalCDs + totalVinyls;
```

A l'inverse pour les soustraire, il faut utiliser le signe `-`

```js
let cookiesInJar = 10;
let cookiesRemoved = 2;
 
let cookiesLeftInJar = cookiesInJar - cookiesRemoved;
```

Pour ajouter ou soustraire un nombre d'une variable, il est possible d'utiliser les opérateurs `+=` & `-=` ce qui donne :

```js
let cookiesInJar = 10;

/* manger deux cookies */
cookiesInJar -= 2;  //il reste 8 cookies

/* cuisson d'un nouveau lot de cookies */
cookiesInJar += 12; // il y a maintenant 20 cookies dans la boîte
```

Il est également possible d'utiliser les opérateurs `++` & `--` pour ajouter ou soustraire 1 (incrément ou décrément)

```js
let numberOfLikes = 10;

numberOfLikes++;  // cela fait 11

numberOfLikes--; // et on revient à 10...
```

**LES MULTIPLICATIONS & LES DIVISIONS**

Pour faire des multiplications & des divisions il faut utiliser les opérateurs `*` & `/`

exemple :

```js
let costPerProduct = 20;
let numberOfProducts = 5;

let totalCost = costPerProduct * numberOfProducts;

let averageCostPerProduct = totalCost / numberOfProducts;
```

Tout comme pour les additions & les soustractions, il existe les opérateurs `*=` & `/=` pour multiplier ou diviser un nombre :

```js
let numberOfCats = 2;

numberOfCats *= 6;  // numberOfCats vaut maintenant 2*6 = 12; 

numberOfCats /= 3;  // numberOfCats vaut maintenant 12/3 = 4;
```

### Qu'est ce qu'une constante ?

Certaines données (nom d'une entreprise, date de naissance d'un utilisateur ...) ne doivent pas être modifiées durant l'exécution d'un programme, il faut donc les assigner à des constantes pour ne pas leur réaffecter de nouvelles valeurs.

Pour créer une constante, il faut commencer par la déclarer en utilisant le mot clef *const* suivi du nom de la constante.

Exemple :

```js
const hoursPerDay = 24;
const minutesPerHour = 60;
const secondsPerMinute = 60;
```

### Qu'est ce qu'un type ?

Le **type** d'une variable ou d'une constante = le genre des données qu'elle enregistre.  En JavaScript, il y a trois types primitifs (= les briques de base de chaque structure de données en JavaScript) principaux :

- number (nombre)
- string (chaîne de caractères)
- boolean (valeur logique)

Les variables de type `number` peuvent être positives, négatives, entières (integers) ou bien décimales (loating-point pour nombre à virgule)

:warning: L'arithmétique en virgule flottante peut déclencher des erreurs :warning:

Les valeurs logiques (booleans) = les + simples car elles ne peuvent avoir que 2 valeurs `true` ou `false`

exemple :

```js
let userIsSignedIn = true;
let userIsAdmin = false;
```

Les chaînes de caractères ou *strings* permettent d'enregistrer du texte dans des variables en utilisant les guillemets simples ou doubles

exemple :

```js
let firstName = "Will";
let lastName = 'Alexander';
```

Il est possible de concaténer des chaînes de caractères en utilisant l'opérateur `+`

```js
let wholeName = firstName + " " + lastName;  // valeur: "Will Alexander"
```

:warning: Faire attention aux types des variables & privilégier au maximum les constantes quand cela = possible :warning:

## Les objets & les classes

Les objets en JavaScript = écrits en **JSON** (JavaScript Object Notation) --> séries de paires **clefs/valeurs** séparées par des `,` les tout mis entre `{}`

Il est possible d'enregistrer des objets dans des variables :

```js
let myBook = {
    title: 'The Story of JS',
    author: 'J. Doe',
    numberOfPages: 300,
    isAvailable: true
};
```

Une fois qu'un objet = enregistré dans 1 variable, il est possible d'avoir accès à ses données en utilisant le nom de la variable, un point (`.`) et enfin le nom de la clef que l'on souhaite récupérer :

```js
let myBook = {
    title: "The Story of JS",
    author: "J. Doe",
    numberOfPages: 300,
    isAvailable: true
};

let bookTitle = myBook.title;  // "The Story of JS"
let bookPages = myBook.numberOfPages  // 300
```

**LES CLASSES**

1 classe = 1 modèle pour 1 objet dans le code & permet de construire +sieurs obj du même type (*instances*)

Voici un exemple de classe :

```js
class Book {
    constructor(title, author, pages) {
        this.title = title;
        this.author = author;
        this.pages = pages;
    }
}
```

Maintenant que la classe = créée , il est possible de créer des instances avec le mot clef `new`

```js
let myBook = new Book("The Story of JS", "J. Doe", 300);
```

ce qui va créer l'objet :

```js
{
    title: "The Story of JS",
    author: "J.Doe",
    pages: 300
}
```

## Les array ou tableaux

Pour créer un tableau, il faut utiliser des crochets `[]` comme par exemple :

```js
let guests = ["Sarah Kate", "Audrey Simon", "Will Alexander"];
```

Il est possible d'accéder aux différents éléments d'un tableau en utilisant les indices (ces derniers démarrent à 0)

```js
let firstGuest = guests[0]; // "Sarah Kate"
let thirdGuest = guests[2]; // "Will Alexander"
let undefinedGuest = guests[12] // undefined
```

:warning:
En JavaScript, les types primitifs tels que les nombres, les valeurs logiques et les chaînes sont passés par **valeur**. A l'inverse, les objets et les tableaux sont passés par **références**.
:warning:

La propriété `length`indique le nombre d'élément que contient un tableau

exemple :
```js
let guests = ["Jon Doe", "Sarah Kate", "Audrey Simon"];

let howManyGuests = guests.length; // 3
```

:warning: ne pas oublier `.` avant `length` pour accéder à la propriété


Pour ajouter un élément dans un tableau, il faut utiliser la propriété `.push` (l'élément se trouvera à la fin du tableau) ou `.unshift`(l'élément se trouvera en haut du tableau)

exemples :
```js
guests.push("Tao Perkington"); // ajoute "Tao Perkington" à la fin de notre tableau guests
```

ou

```js
guests.unshift("Tao Perkington"); // "Tao Perkington" est ajouté au début du tableau guests
```

pour supprimer 1 élément, il faut utiliser la propriété `pop`sans passer aucun argument

exemple :

```js
guests.pop(); // supprimer le dernier élément du tableau
```

- Un **set** = liste non ordonnée
- Une **map** = liste ordonnée de paires clefs/valeurs

Le JavaScript fonctionne dans différents environnements comme par exemple le JSBin, les environnements web et les serveurs ....


## Les instructions If & Else

Les instructions If/Else sont des instructions conditionnelles

Si on utilise des `boolean`simple, il faut utiliser cette syntaxe :

```js
if (myBoolean) {
    // réaction à la valeur vraie de myBoolean
} else {
    // réaction à la valeur faux de myBoolean
}
```

donc pour vérifier qu'un utilisateur est connecté il faut écrire ce morceau de code :

```js
let userLoggedIn = true;

if (userLoggedIn) {
    console.log("Utilisateur connecté!");
} else {
    console.log("Alerte, intrus!");
}
```


Avec If & Else, il est possible d'utiliser des expressions de comparaison afin de comparer deux valeurs comme par exemple :

- `<` inférieur à ;
- `<=`inférieur ou égal à ;
- `==`égal à ;
- `>=`supérieur ou égal à ;
- `>` supérieur à ;
- `!=`différent de.

Ce qui donne :

```js
const numberOfSeats = 30;
let numberOfGuests = 25;

if (numberOfGuests < numberOfSeats) {
    // autoriser plus d'invités
} else {
    // ne pas autoriser de nouveaux invités
}
```
Il est possible de chaîner des instructions `If`/`Else` pour réagir à des conditions potentielles multiples :

```js
if (numberOfGuests == numberOfSeats) {
    // tous les sièges sont occupés
} else if (numberOfGuests < numberOfSeats) {
    // autoriser plus d'invités
} else {
    // ne pas autoriser de nouveaux invités
}
```

En JavaScript, toutes les égalités ne sont pas nées égales :

Il y a 2 façons de vérifier si 2 valeurs sont égales en JavaScript :  `==` et  `===`, aussi appelées égalité simple et égalité stricte :

- l'égalité simple vérifie la valeur, mais pas le type. Donc ceci renvoie la valeur  `true`:
`5 == "5"`
- par contre, l'égalité stricte vérifie à la fois la valeur et le type. Donc :`5 === "5"`renvoie  `false`, car on compare un  `number` à un  `string`.

De même, il y a 2  opérateurs d'inégalité  `!=` et  `!==`, avec la même distinction.


Les conditions dites multiples :

- `&&` **ET** logique --> vérifier que si 2 conditions = **toutes les 2 vraies**
- `||` **OU** logique -->  vérifier qu'**au moins 1 condition = vraie**
- `!` **NON** logique --> vérifier si 1 condition n'est pas vraie

exemple :

```js
let userLoggedIn = true;
let userHasPremiumAccount = true;
let userHasMegaPremiumAccount = false;

userLoggedIn && userHasPremiumAccount; // true
userLoggedIn && userHasMegaPremiumAccount; // false

userLoggedIn || userHasPremiumAccount; // true
userLoggedIn || userHasMegaPremiumAccount; // true

!userLoggedIn; // false
!userHasMegaPremiumAccount; // true
```

Un bloc de code ou bloc = une section de code incluse entre accolades  `{}`.

Pour que le code fonctionne correctement, il faut déclarer les variables au début puis écrire en dessous les conditions avec `If`/`Else`

exemple :

```js
let userLoggedIn = true;
let welcomeMessage = ''; // déclarer la variable ici

if (userLoggedIn) {
    welcomeMessage = 'Welcome back!'; // modifier la variable extérieure
} else {
    welcomeMessage = 'Welcome new user!'; // modifier la variable extérieure
}

console.log(welcomeMessage); // imprime 'Welcome back!'
```

La variable = déclarée dans le scope parent, elle = disponible partout, accessible et peut être modifiée correctement.


Pour vérifier une variable, il est possible d'utiliser l'instruction `switch`

## Les boucles For & While

La boucle `For` permet de savoir "combien de fois ?"

Pour commencer, il faut déclarer une variable, par exemple le nombre de passagers puis créer une variable d'indice `i` permettant de compter le nombre d'exécutions de la boucle (:warning: **il faut commencer à 0**). La deuxième condition à mettre dans la boucle `for` = **tant que i < au nombre de passagers alors continuer**. La dernière condition à ajouter = si i < au nombre de passagers alors passer au suivant (i++)

En code cela donne :

```js
const numberOfPassengers = 10;

for (let i = 0; i < numberOfPassengers; i++) {
    console.log("Passager embarqué !");
}
```
