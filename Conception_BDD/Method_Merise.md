Webcadors : Conception BDD

Besoins des futurs utilisateurs : 

1. Développeur (non-inscrit) :

Pour chaque développeur non-inscrit, il doit juste pouvoir naviguer et consulter des offres sur le site;
Il doit pouvoir s’inscrire;

2. Développeur (inscrit) : 

   On doit connaître son identité, expériences, photos, recommandations, vidéos;
On doit connaître ses qualifications;
Il doit pouvoir faire une candidature spontanée qui ne vise aucune offre ou entreprise;
Il doit pouvoir répondre à une ou plusieurs offres (postuler);
Il peut recevoir une demande de chat ou de vidéoconférence par une ou plusieurs entreprises premium;
Il peut être contacté et contacter une ou plusieurs entreprises inscrite/premium;

3. Entreprise (non-inscrite) :

Pour chaque entreprise non-inscrit, il doit juste pouvoir naviguer et consulter des candidatures/profils sur le site;
Elle doit pouvoir s’inscrire;

4. Entreprise (inscrite) :

On doit connaître son identité, expériences, photos, recommandations, vidéos;
Elle doit pouvoir poster une ou plusieurs offres d’emploi;
Elle doit pouvoir devenir Premium;

5. Entreprise (premium) :

Avoir les avantages des entreprises inscrites;
Elle a le droit de créer un chat et de faire des vidéoconférences avec des développeurs inscrits;
Elle a le droit d’avoir de l’aide pour les suggestions de salaires, grâce aux statistiques salariales mondiales; 
Elle peut faire passer des tests par « codeshare.io »;
Elle peut formuler des propositions d’embauche selon un salaire spécifique, que le développeur accepte, sinon l’entreprise a la possibilité d’en reformuler une ainsi de suite.

















Le dictionnaire des données

Code mnémonique
Désignation
Type
Taille
Remarque
DEVELOPPEUR




id_dev 
Identifiant du développeur inscrit
N


nom_dev
Nom du développeur inscrit
A
30

prenom_dev
Prénom du développeur inscrit
A
30

date_naissance_dev
Date de naissance du développeur inscrit
DATE

Au format JJ-MM-AAAA
adresse_dev
Adresse du développeur inscrit
AN
50

ville_dev
Ville du développeur inscrit
A
50

cp_dev
Code postal du développeur inscrit
N
5
Géolocalisation
tel_dev
Téléphone du développeur inscrit
N
15

email_dev
Mail du développeur inscrit
AN
100

pswd_dev
Mot de passe du développeur inscrit
AN
30
Minimum 6 caractères
domaine_dev
Domaine d’activité du développeur inscrit
A
30
Auto-complétion
description_dev
Description du développeur inscrit
AN
1000

titre_experience_dev
Titre de l’expérience du développeur inscrit
AN
5000

debut_experience_dev
Date du début de l’expérience du développeur inscrit
DATE

Au format JJ-MM-AAAA
fin_experience_dev
Date de fin de l’expérience du développeur inscrit
DATE

Au format JJ-MM-AAAA
contenu_experience_dev
Descriptif de l’expérience du développeur inscrit
AN
2000

domaine_experience_dev
Domaine de l’expérience du développeur inscrit
A
30
Auto-complétion
recommandations_recues_dev
Recommandations reçues par le développeur inscrit
AN
1000

recommandations_envoyees_dev
Recommandations envoyées par le développeur inscrit
AN
1000

photos_dev
Photos du développeur inscrit



videos_dev
Vidéos du développeur inscrit



ENTREPRISE STANDARD




id_entreprise
Identifiant de l’entreprise inscrite
N


nom_entreprise
Nom de l’entreprise inscrite
A
100

numero_siret_entreprise
Numéro SIRET de l’entreprise inscrite
N
15

numero_tva_entreprise
Numéro de TVA de l’entreprise inscrite
AN
15

adresse_entreprise
Adresse de l’entreprise inscrite
AN
50

ville_entreprise
Ville de l’entreprise inscrite
A
50

cp_entreprise
Code postal de l’entreprise inscrite
N
5

tel_entreprise
Telephone de l’entreprise inscrite
N
15

effectif_entreprise
Taille de l’entreprise inscrite
N
6

domaine_entreprise
Domaine d’activité de l’entreprise inscrite
A
30
Dans un menu déroulant avec possibilité de choix multiples
description_entreprise
Description de l’entreprise inscrite
AN
1000

historique_projets_entreprise
Historique des projets de l’entreprise inscrite
AN
2000

titre_historique_projets_entreprise
Titre du projet de l’entreprise inscrite
AN
5000

date_historique_projets_entreprise
Date du projet de l’entreprise inscrite
DATE

Au format JJ-MM-AAAA
contenu_historique_projets_entreprise
Descriptif du projet de l’entreprise inscrite
AN
2000

domaine_historique_projets_entreprise
Domaine du projet de l’entreprise inscrite
A
30
Auto-complétion
photos_entreprise
Photos de l’entreprise inscrite



videos_entreprise
Vidéos de l’entreprise inscrite


Facultatif
titre_offre_entreprise
Titre de l’offre d’emploi proposée par l’entreprise
A
30

date_parution_offre_entreprise
Date de parution de l’offre d’emploi proposée par l’entreprise
DATE

Au format JJ-MM-AAAA
description_offre_entreprise
Description de l’offre d’emploi proposée par l’entreprise
AN
1032

ENTREPRISE PREMIUM




acces_videoconf_premium
Accès à la vidéo conférence entre l’entreprise premium et le(s) développeur(s) de son choix
Boolean


chat_premium
Messages envoyés aux destinataires inscrits par l’entreprise premium
AN
1032
Service externe
acces_codeshare.io_premium
Accès à la plateforme codeshare.io pour l’entreprise premium
Boolean


bdss_premium
Accès à bdss pour l’entreprise premium
Boolean




Modèle Logique de Données (MLD)


