# Créer un site responsive avec Bootstrap 4

Pour commencer il faut écrire cette ligne de code dans le `<head>` du fichier HTML (avant le reste des fichiers CSS, afin que nos styles remplacent ceux de Bootstrap par défaut.)

```HTML
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/css/bootstrap.min.css" integrity="sha384-Vkoo8x4CGsO3+Hhxv8T/Q5PaXtkKtu6ug5TOeNV6gBiFeWPGFN9MuhOf23Q9Ifjh" crossorigin="anonymous">
```

Il faut également ajouter les informations suivantes en bas de la page HTML

```HTML
<!-- jQuery first, then Popper.js, then Bootstrap JS -->
<script src="https://code.jquery.com/jquery-3.4.1.slim.min.js" integrity="sha384-J6qa4849blE2+poT4WnyKhv5vZF5SrPo0iEjwBvKU7imGFAV0wwj1yYfoRSJoZ+n" crossorigin="anonymous"></script>
<script src="https://cdn.jsdelivr.net/npm/popper.js@1.16.0/dist/umd/popper.min.js" integrity="sha384-Q6E9RHvbIyZFJoft+2mJbHaEWldlvI9IOYy5n3zV9zzTtmI3UksdQRVvoxMfooAo" crossorigin="anonymous"></script>
<script src="https://stackpath.bootstrapcdn.com/bootstrap/4.4.1/js/bootstrap.min.js" integrity="sha384-wfSDF2E50Y2D1uUdj0O3uMBJnjuUD4Ih7YwaYd1iqfktj0Uod8GCExl3Og8ifwB6" crossorigin="anonymous"></script>
```


Sur un site web, une zone **hero** permet de mettre en valeur un élément central tel qu’un titre, un call-to-action (un appel à l’action), ou tout message important afin d’attirer l’œil de vos utilisateurs. Cette technique permet de créer une réelle séparation avec le reste du contenu. Une zone **hero** est souvent composée de marges internes importantes et d’une image d’arrière-plan permettant d’accentuer la portée du message central.


## Apprendre à utiliser la grille Bootstrap

Depuis la version 4 Bootstrap utilise la fonction Flexbox pour répartir le contenu sur la page

Mettre l'ensemble des infos de la page dans la class : `container` ou `container-fluid` s'il on souhaite que le contenu prenne 100% de l'espace dispo de la page.

Bootstrap 4 possède un système de grille puissant et flexible qui permet de créer tous les types de mise en page. Cette grille utilise une série de lignes et de colonnes pour mettre en page le contenu. Une ligne permet d’envelopper une ou plusieurs colonnes qui intègrent du contenu.

Répartir les éléments de la manière suivante :

```HTML
<div class="container-fluid">
     <div class="row">
        <div class="col">
           Première colonne
        </div>
        <div class="col">
           Deuxième colonne
        </div>
     </div>
     <div class="row">
        <div class="col">
           Première colonne
        </div>
        <div class="col">
           Deuxième colonne
        </div>
        <div class="col">
           Troisième colonne
        </div>
     </div>
  </div>
```

Une page responsive est une page qui réagit à différentes tailles d'écran de l'utilisateur, en modifiant la mise en page des composants et du contenu à ajuster.

https://openclassrooms.com/fr/courses/6391096-creez-des-sites-web-responsive-avec-bootstrap-4/6503577-rendez-votre-mise-en-page-responsive#/id/r-6895384 (lien vers les différents points d'arrêt gérés par bootstrap)
