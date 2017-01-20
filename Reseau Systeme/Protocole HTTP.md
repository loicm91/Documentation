#Liste des codes HTTP

En informatique, le code HTTP (aussi appelé code de statut) permet de déterminer le résultat d'une requête ou indiquer au client une erreur. 
Ce code numérique est destiné aux traitements automatiques par les logiciels de client HTTP. 
Ces codes de statuts ont été spécifiés par la RFC 26161, en même temps que d’autres codes de statuts, non normalisés mais très utilisés sur le web. 
Ils ont été ensuite étendus 
par la RFC 72312.

Le premier chiffre du code de statut est utilisé pour spécifier une des cinq catégories de réponse (informations, succès, redirection, erreur client et erreur serveur). 
Les codes les plus courants sont :

###200 : succès de la requête ;


###301 et 302 : redirection, respectivement permanente et temporaire ;
(ex : Get de /toto, moi je lui renvoi un code 302 pour aller sur la page /titi)
###301 : Surtout utiliser pour des solutions de référencements.

###304 : la page vient du cache.

##Erreur d'utilisation:

###401 : utilisateur non authentifié ;
###403 : accès refusé ;
###404 : page non trouvée ou n'existe pas;

##Erreur technique : 

###500 et 503 : erreur serveur.

Certains codes ne sont pas encore utilisés, mais sont projetés pour une utilisation future. D'autres codes n'entraînent aucun affichage spécifique pour l’utilisateur, 
mais sont sous-entendus (par exemple, le code 200 ou 304, jamais vu par le client car ils concernent la majorité des requêtes réussies).




#METHOD

Dans le protocole HTTP, une méthode est une commande spécifiant un type de requête, c'est-à-dire qu'elle demande au serveur d'effectuer une action. 
En général l'action concerne une ressource identifiée par l'URL qui suit le nom de la méthode.

Dans l'illustration ci-contre, une requête GET est envoyée pour récupérer la page d'accueil du site web www.perdu.com :

###GET / HTTP/1.1
Host: www.perdu.com
Il existe de nombreuses méthodes, les plus courantes étant GET, HEAD et POST :

###GET
C'est la méthode la plus courante pour demander une ressource. Une requête GET est sans effet sur la ressource, il doit être possible de répéter la requête sans effet.
Rentre automatiquement dans le cache du navigateur.


###HEAD
Cette méthode ne demande que des informations sur la ressource, sans demander la ressource elle-même (body dans le html).


###POST
Cette méthode est utilisée pour transmettre des données en vue d'un traitement à une ressource (le plus souvent depuis un formulaire HTML). 
L'URI fourni est l'URI d'une ressource à laquelle s'appliqueront les données envoyées. 
Le résultat peut être la création de nouvelles ressources ou la modification de ressources existantes. 
À cause de la mauvaise implémentation des méthodes HTTP (pour Ajax) par certains navigateurs 
(et la norme HTML qui ne supporte que les méthodes GET et POST pour les formulaires), 
cette méthode est souvent utilisée en remplacement de la requête PUT, qui devrait être utilisée pour la mise à jour de ressources.

Un POST sert à créer une information.(ex : création d'un utilisateur)


###OPTIONS
Cette méthode permet d'obtenir les options de communication d'une ressource ou du serveur en général.


###CONNECT
Cette méthode permet d'utiliser un proxy comme un tunnel de communication.


###TRACE
Cette méthode demande au serveur de retourner ce qu'il a reçu, dans le but de tester et effectuer un diagnostic sur la connexion.


###PUT
Cette méthode permet de remplacer ou d'ajouter une ressource sur le serveur. L'URI fourni est celui de la ressource en question.
(ex : remplacer/modifier les informations d'un utilisateur)


###PATCH
Cette méthode permet, contrairement à PUT, de faire une modification partielle d'une ressource.
(ex : modifier juste une donnée ou quelques données pour en envoyer le moins possible)


###DELETE
Cette méthode permet de supprimer une ressource du serveur.
Eviter de le rentrer dans le cache de l'ordinateur.


Ces 3 dernières méthodes nécessitent généralement un accès privilégié.

Certains serveurs autorisent d'autres méthodes de gestion de leurs ressources (par exemple WebDAV).
