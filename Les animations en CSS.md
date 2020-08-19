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
