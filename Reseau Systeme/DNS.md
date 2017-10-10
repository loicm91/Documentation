# DNS

## Registrar : 
Gandi et OVH sont des registrar qui permettent d'acheter des noms de domaines avec des extensions comme ".com"; ."fr"; ".net"

## DNS : 
Domain Name Service, c'est le nom de domaine qui permet d'établir les correspondances entre les noms de domaine et les adresses IP.
Ce sont les serveurs de noms de domaine qui permettent aux internautes de saisir des URL et non des adresses IP dans la barre d’adresse des navigateurs.

## Subdomain : 
Un sous domaine est une forme particulière d’extension d’un nom de domaine qui précède un nom de domaine.
Par exemple, affilation.www.definitions-marketing.com pourrait être un sous domaine du domaine www.definitions-marketing.com.

Plusieurs centaines ou milliers de sous-domaines peuvent être créés pour un même domaine. La création de sous-domaines ne nécessite pas de procédure de dépôt particulière et relève d’une simple procédure ou niveau de l’interface de gestion du service d’hébergement du domaine principal. Il s’agit généralement d’un service gratuit.

La création de sous-domaines peut présenter un intérêt dans le cadre de l’optimisation du référencement naturel. Elle permet en effet, au même titre que la création de répertoires, de faire apparaître des mots clés cibles dans l’URL. Par ailleurs, certains moteurs ou annuaires peuvent considérer des sous-domaines comme des domaines différents et ainsi permettre de multiplier les occasions d’affichage dans les résultats.

Il semble cependant que la création de sous-domaines a de moins en moins d’impact pour l’optimisation du référencement sur Google.
La présence de sous-domaines peut également être utilisée à des fins de répartition de charges sur des serveurs lors de pics de trafic.

## Acheter et Configurer le nom de domaine :
Créer un compte sur Ovh et ensuite le valider puis choisir un ".com".

### Configuration du DNS :
Cliquer sur le nom de domaine choisi, puis Zone DNS.
Cliquer sur 'Ajouter une entrée DNS'
Deux choix : soit faire un pointage avec 'A' et rentrer une adresse IP qui si à l'avenir on souhaite changer de serveur va garder le même lien vers le nom de domaine, soit CNAME avec l'adresse de l'autre hôte (ex : vps355203.ovh.net.) avec le point final.

Si on ne tombe pas sur la bonne page, il Faut reconfigurer le Virtual Host pour qu'il appelle la bonne page :

```
<VirtualHost *:80>
DocumentRoot /var/www/html/code-closet/public/
ServerName code-closet.com
        <Directory /var/www/html/code-closet/public/>
                AllowOverride All
        </Directory>
</VirtualHost>
```

