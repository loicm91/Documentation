#Mémo concepts Php Objet Orienté - POO

##Attributs : 
####Les variables au sein d'une classe sont appelées "propriétés". On peut également les retrouver sous les dénominations "attributs", "membres" ou "champs". Elles sont définies en utilisant un des mots-clés public, protected, ou private, suivi d'une déclaration classique de variable. Cette déclaration peut comprendre une initialisation, mais celle-ci doit être une valeur constante, c'est à dire qu'elle doit pouvoir être évaluée pendant la compilation du code, et qu'elle ne peut pas dépendre d'informations déterminées lors de l'exécution de celui-ci pour pouvoir être évaluée.

##Getter :
####C'est une méthode qui permet de récupérer une valeur et aussi de la modifier.

##Setter : 
####C'est une méthode qui permet de vérifier une donnée avant d'être stockée.

##Instancier : 
####C'est la création d'un objet qui va dépendre d'une Class. ex : $perso = new Personnage, $perso sera un objet de type Personnage (qui est la Class)
'function __construct()':
C'est le constructeur de la classe, soit la fonction qui s'exécute automatiquement et qui permet d'exploiter les variables que tu peux passer quand tu instancies ta classe.

##Héritage/ inheritance :
####L'héritage est un des grands principes de la programmation orientée objet (POO), et PHP l'implémente dans son modèle objet. Ce principe va affecter la manière dont de nombreuses classes sont en relation les unes avec les autres.

Par exemple, lorsque vous étendez une classe, la classe fille hérite de toutes les méthodes publiques et protégées de la classe parente. Tant qu'une classe n'écrase pas ces méthodes, elles conservent leur fonctionnalité d'origine.

L'héritage est très utile pour définir et abstraire certaines fonctionnalités communes à plusieurs classes, tout en permettant la mise en place de fonctionnalités supplémentaires dans les classes enfants, sans avoir à réimplémenter en leur sein toutes les fonctionnalités communes.

##Surcharger / overriding :
####Si une Class override les méthodes qui sont héritées, elles (les méthodes) garderont leurs fonctionnalités de départ.
