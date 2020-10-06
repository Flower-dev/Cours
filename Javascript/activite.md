Suite à votre travail sur le site de streaming, on vous demande de créer une app appelée RestfulReading, qui permettra aux utilisateurs de suivre les livres qu'ils sont en train de lire/qu'ils ont lus.

Votre tâche est de créer la classe  Book (Livre) et de peupler la base de données de développement de trois ou quatre livres pour vous assurer que l'interface fonctionne correctement (vous travaillerez avec le fichier  Book.js  ).

La classe  Book  doit contenir les champs suivants :

title  -  string  - le titre du livre
author  -  string  - l'auteur du livre
description  -  string  - une description du livre
pages  -  number  - le nombre total de pages
currentPage  -  number  - la page où se trouve l'utilisateur actuellement (entre 1 et  pages  )
read  -  boolean  - si l'utilisateur a lu ou non le livre (par défaut:  false  )
La classe  Book  doit aussi contenir la méthode instance suivante :

readBook(page)
permet à l'utilisateur de dire à quelle page il se trouve actuellement
si l'argument  page  est inférieur à un ou supérieur au nombre total de pages du livre, readBook retourne  0
si l'argument  page  est supérieur ou égal à 1 et inférieur au nombre total de pages du livre,  readBook  modifie le champ  currentPage  de l'instance pour être égal à la valeur de l'argument passé, et retourne 1
si l'argument  page  est égal au nombre total de pages du livre,  readBook  modifie le champ  currentPage  de l'instance pour être égal à la valeur de l'argument passé, modifie le champ  read  de l'instance en  true  , et retourne  1
Quand vous aurez créé la classe  Book  , vous en créerez au moins trois instances valables et vous les mettrez dans le tableau  books  qui est exporté par  Book.js  . Pour vérifier votre travail, actualisez le navigateur Codevolve intégré : vos instances  Book  devraient être visibles dans le carousel de l'interface RestfulReading.

Pour tester votre méthode instance  readBook  , suivez ces instructions pour trois livres (sans rafraîchir la page) :

mettez à jour la page actuelle avec une page valable qui est inférieure au nombre total de pages
mettez à jour la page actuelle avec exactement le nombre de pages total du livre (le livre devrait disparaître du carousel et apparaître dans la liste "Lus")
