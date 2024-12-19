# Identification du projet 
## Nom et titre du Projet 

**SecureIntimacy** : Plateforme de Protection des images privées contre leurs diffusion non consensuelle.

## Brève description du projet 

SecureIntimacy est une plateforme innovante dédiée à la protection des individus contre la diffusion non consensuelle de leurs images intimes. Le système repose sur la génération d'empreintes numériques uniques (hash) pour chaque image soumise, facilitant leur comparaison avec des bases de données partenaires. En cas de correspondance, l'utilisateur est immédiatement alerté et peut décider des actions à entreprendre pour protéger sa vie privée.

## Public ciblé/Clients potentiels :

- **Public ciblé** : Les utilisateurs soucieux de leur vie privée et de la protection de leurs données personnelles, notamment dans les contextes de partage de contenus intimes.
- **Clients potentiels** : Des entreprises, des plateformes de médias sociaux et des services de messagerie souhaitant intégrer des mécanismes de prévention contre la diffusion non consensuelle de contenus intimes, ainsi que des organisations de protection des droits numériques, Aussi les célébrités, les influenceurs et les personnalités publiques qui partagent fréquemment des contenus intimes sur les plateformes numériques et qui sont particulièrement vulnérables à la diffusion non consensuelle de ces contenus.

## Demo 
### 	Définition des exigences fonctionnelles

- 	Créer un cas et générer un hash : L'utilisateur peut soumettre une image ou une vidéo, ce qui déclenche la génération d'une empreinte numérique (hash) côté client à l’aide d’un algorithme de phash. Cet hash, unique pour chaque fichier, est ensuite associé à un cas afin que l’utilisateur puisse facilement l'identifier. Il est ensuite stocké et utilisé pour comparer les contenus avec ceux des bases de données partenaires.
- 	Lister les cases : L'utilisateur peut consulter la liste des empreintes numériques qu'il a soumises. Cette fonctionnalité permet de suivre l'historique des fichiers soumis pour une gestion efficace des contenus potentiellement sensibles.
-  visualiser les détails d’un cas et l'historique des correspondances de hashes : Chaque utilisateur peut consulter les détails de chaque hash, y compris l'historique des correspondances détectées avec les bases de données partenaires. Cela permet une traçabilité complète et un suivi des actions entreprises en cas de correspondance.

- Automatiser la surveillance et l’envoie d'alertes : Un système automatisé scanne en continu les bases de données partenaires pour rechercher des correspondances avec les hashes des utilisateurs. Si une correspondance est trouvée, une alerte est envoyée à l'utilisateur concerné, lui permettant de prendre des mesures immédiates pour protéger sa vie privée.
- S’authentification de manière sécurisée :   Un système d'authentification utilisant des JSON Web Tokens (JWT) est mis en place pour garantir que seuls les utilisateurs autorisés puissent accéder à la plateforme. Cela assure la sécurité des données et la confidentialité des actions de l'utilisateur.
Avant de commencer le développement, le backlog de développement a été rédigé dans Jira. Ce backlog contient toutes les fonctionnalités et tâches nécessaires et réalisées dans la mise en œuvre de la plateforme SecureIntimacy. Il permet de structurer le travail en sprints et de prioriser les différentes étapes du projet, garantissant ainsi une progression continue et une gestion efficace des ressources. 

 ![image](https://github.com/user-attachments/assets/4921abde-da6b-48a6-83bf-0f085811e69d)

### 	Définition des exigences techniques
-	Scalabilité : La plateforme doit être capable de gérer une augmentation du nombre d'utilisateurs et de données sans perte de performance. La solution doit pouvoir évoluer horizontalement, avec l'ajout de serveurs ou de ressources en fonction de la demande. L'infrastructure cloud permettra une mise à l'échelle flexible et réactive.
-	Haute disponibilité : Afin d'assurer une disponibilité continue, la plateforme doit être déployée dans un environnement haute disponibilité (HA), avec des mécanismes de redondance pour les composants critiques, comme les bases de données et les serveurs d'authentification.
-	Sécurité des données : Toutes les données sensibles, y compris les empreintes numériques (hashes) et les informations des utilisateurs, doivent être stockées et transmises de manière sécurisée. Cela inclut l’utilisation du chiffrement AES pour le stockage des données et des connexions HTTPS pour sécuriser la transmission des données.
-	Traitement des données en temps réel : Le système doit être capable de scanner en temps réel les bases de données partenaires pour détecter toute correspondance avec les hashes des utilisateurs. Cela nécessite l'utilisation d'un moteur de traitement efficace et réactif pour comparer les empreintes numériques rapidement.
-	Performances et optimisation : La plateforme doit garantir un faible temps de latence, notamment pour la génération des hashes et les comparaisons avec les bases de données partenaires. Des mécanismes de mise en cache et d'optimisation des requêtes doivent être utilisés pour améliorer la réactivité du système.
-	Conformité avec les normes de confidentialité : La plateforme doit respecter les normes et régulations de confidentialité des données, telles que le RGPD (Règlement Général sur la Protection des Données). Cela inclut la gestion des consentements utilisateurs et la possibilité pour les utilisateurs de supprimer ou de modifier leurs données personnelles.
-	Mise à jour et maintenance : Le système doit être conçu de manière modulaire pour faciliter les mises à jour régulières et la maintenance. L’architecture du projet devra permettre l'intégration de nouvelles fonctionnalités sans affecter les fonctionnalités existantes.
-	Surveillance et logs : Des outils de surveillance doivent être mis en place pour suivre les performances de la plateforme et détecter les anomalies. De plus, des logs détaillés des actions des utilisateurs et des systèmes doivent être collectés pour permettre un suivi complet et une gestion des incidents.
Ces exigences techniques assureront que SecureIntimacy puisse répondre aux besoins des utilisateurs tout en garantissant un environnement sécurisé, scalable et performant.

### Choix techniques 
![image](https://github.com/user-attachments/assets/2094dd27-5318-4476-b1ae-97c86dd83255)

### Architecture logicielle 

![image](https://github.com/user-attachments/assets/e6f7d080-e8bf-436a-8b22-012502ac6da7)
 
### 	Conception et réalisation

#### Premier Sprint 
 
La figure ci-dessous illustre les différentes tâches réalisées durant le premier sprint, d'une durée de 24 jours
##### 	Diagramme de UseCase
  
![image](https://github.com/user-attachments/assets/d24882a5-a11d-4ca6-acd3-7affd295586f)

#####  Diagramme de Classe

Ci-dessous le diagramme de classe représentant les données des entités Case et Hash et User en particuliers nécessaires pour les premières fonctionnalités comme est indiqué :
   ###### La classe **Case** contient un identifiant caseNumber, la date de création du dossier createDate, ainsi qu'une description de l’image téléchargée description, facilitant l’identification du dossier après sa création. Elle inclut également le titre du dossier et un PIN unique pour chaque cas, garantissant ainsi qu'il n'y ait aucune confusion ultérieure. Ce PIN sera envoyé par notification après la création du cas. En outre, cette classe agit comme le contrôleur du système, interagissant avec la plupart des fonctionnalités liées à la gestion des cas.

  ![image](https://github.com/user-attachments/assets/9c16fd6a-864a-404d-8e36-33a4c673896a)
  ###### La classe **Hash** contient des informations sur le hachage généré, notamment sa valeur hashValue et la date de sa création creationDate. Il est important de noter qu'il n'y a pas de méthode createHash, car le hachage est effectué côté client en utilisant l'algorithme de Perceptual Hashing. Cet algorithme est implémenté en appelant la bibliothèque image-hash, installée via npm install image-hash. 
  ######  La classe **User** contient les informations essentielles concernant l'utilisateur, permettant de gérer l'affichage des cas et la liste des cas associés à l'utilisateur
  - Le **Perceptual Hashing** est une technique qui génère un "empreinte" numérique d'une image en comparant ses caractéristiques visuelles plutôt que de simplement examiner ses données binaires. Cela permet de détecter des images similaires, même si elles sont modifiées (par exemple, redimensionnées ou légèrement altérées). Cette approche est particulièrement utile pour identifier les copies d'images sans se baser sur une correspondance exacte, La complexité temporelle de la génération du Perceptual Hash est O(n), où n est la taille del'image (nombre de pixels), avec un ajustement possible en fonction de la taille du hachage et de la précision choisie et pour la complexité mémoire elle est faible, car elle dépend uniquement de la taille du hachage, qui est généralement petit (environ 64 bits ou 256 bits).

- 	Démonstration 
SecureIntimacy répond à plusieurs exigences techniques, en se concentrant particulièrement sur la flexibilité d'utilisation et l'amélioration de l'expérience utilisateur. Ce projet a été conçu pour offrir une interface fluide et intuitive, permettant à l'utilisateur d'interagir facilement avec toutes les fonctionnalités essentielles. Voici comment l'expérience utilisateur se déploie à travers les différentes pages et sections du site :
  - Page d'Accueil
![image](https://github.com/user-attachments/assets/a3535225-cc39-4f16-a944-ac6b718bcfda)

  - À propos de nous (About Me)
![image](https://github.com/user-attachments/assets/fc15cc07-fd02-4bc3-99ec-f78ebad7efd1)

  - Contactez-nous (contact-us)
 ![image](https://github.com/user-attachments/assets/b5f2c206-4f24-4d11-b0eb-eddeb0820c71)

Foire aux Questions(FAQ)
 ![image](https://github.com/user-attachments/assets/0d643f1c-242f-4433-8de2-c44c62ba5599)

L’utilisateur peut lister ses cases, en affichant pour chacune le titre, un extrait de la description, et la date de création. Il peut également rechercher un cas par son nom. 
 ![image](https://github.com/user-attachments/assets/572a9c3f-102b-48dd-81c6-a53bbb5e2c0f)

Pour créer une case, je dois insérer un titre, une description de l’image et un PIN unique permettant d'identifier l’image. Ensuite, j'ajoute l’image afin de générer son hash. Cet hash est ensuite envoyé au service backend pour être stocké.
 ![image](https://github.com/user-attachments/assets/458597cf-9930-4c45-a1de-c11c2e83d52b)

Pour garantir l’unicité de chaque hash, il est impossible de créer deux cases pour une même image. Cela est assuré en vérifiant l’existence du hash dans la base de données avant chaque insertion.
 ![image](https://github.com/user-attachments/assets/8c116154-f048-4241-8281-546dac308073)
apres la creation de chaque l'utilisateur sera notifier
![image](https://github.com/user-attachments/assets/2d0b1c98-90f8-4181-9d73-4dc011fcce59)

L’utilisateur peut également supprimer un cas, ce qui entraîne la suppression de l’empreinte associée ainsi que de son historique.
 ![image](https://github.com/user-attachments/assets/d87351ee-d770-494c-b223-cba6c28e9cde)
![image](https://github.com/user-attachments/assets/aa4925e3-b244-4aa3-a1a3-4cdda69fdffe)
####  Deuxième Sprint 
 
 La figure ci-dessous illustre les différentes tâches réalisées durant le deuxième sprint, d'une durée de 25 jours
![image](https://github.com/user-attachments/assets/dd147b20-3398-4552-b39f-6cb6a1472e54)

- 	Diagramme de UseCase général 
Le diagramme de cas d'utilisation générale illustre les fonctionnalités essentielles du système, en intégrant à la fois les processus d’authentification et de gestion de compte, ainsi que les mécanismes de scannage des empreintes et de génération d'alertes, qui font partie des fonctionnalités du deuxième sprint. Il met en évidence deux acteurs principaux, l'utilisateur standard et le système. L'utilisateur standard est responsable de la création d'un compte, de la connexion, de la réinitialisation de son mot de passe, ainsi que de la gestion de ses cas, notamment leur création, recherche et suppression. Le système, quant à lui, prend en charge le scannage des empreintes pour rechercher des correspondances dans les ressources, ainsi que l'envoi d'alertes en cas de correspondances détectées. Ce diagramme permet de visualiser l'interaction entre l'utilisateur et le système tout au long de l'expérience de gestion des cas et de sécurité des images.

![image](https://github.com/user-attachments/assets/d5d7295b-5285-44c2-bfb8-5b86d294ffde)

- 	Diagramme de Classe général 
Ci-dessous le diagramme de classe général du prototype représentant les données des entités Case, Hash, User, et s’ajoute en particuliers les entités Match et Partner, nécessaires pour les fonctionnalités restantes voici une description des différentes classes 
  -	La classe Partner représente les partenaires qui partagent des bases de données de contenu protégé. Elle contient des informations sur les partenaires telles que le nom, les coordonnées et les bases de données de contenu qu'ils fournissent. Cette classe est utilisée pour gérer l'accès aux ressources de ces partenaires et faciliter les comparaisons de hashes avec les leurs. Elle joue un rôle central dans l'intégration du système avec les partenaires externes, en permettant la synchronisation des données et la détection des correspondances potentielles entre les images partagées par les utilisateurs et celles des partenaires.
  -	La classe Case reste le contrôleur principal du système. Elle inclut une méthode getHistory, qui prend en entrée l'identifiant de l’hash et retourne les correspondances trouvées (matchs). De plus, avant de créer un cas pour une image, la méthode isCaseExist est utilisée pour vérifier si l’hash existe déjà dans la base de données. Cela garantit l'unicité de chaque hash et empêche la création de cas dupliqués pour des images identiques ou similaires.
  -	La classe Match représente une correspondance trouvée entre une image téléchargée et une image existante dans la base de données illustratives de partenaire. Elle contient deux propriétés principales alertSent un booléen indiquant si une alerte a été envoyée pour cette correspondance et sourceLink l'URL pointant vers la ressource où la correspondance a été trouvée. La méthode isResentMatch() permet de vérifier si c'est la première fois que cette correspondance est détectée, afin d'envoyer une alerte uniquement si nécessaire, évitant ainsi les notifications redondantes. Cette classe est cruciale pour la gestion des alertes et pour assurer un suivi efficace des correspondances d'images dans le système
   -	La classe User joue le rôle de contrôleur pour les fonctionnalités de gestion des rôles et d'authentification.

 ![image](https://github.com/user-attachments/assets/771ba486-2331-4c17-89ab-1aaec83662a7)


La comparaison entre les hashages du client et du partenaire est effectuée à l'aide d'un algorithme basé sur la **distance de Hamming**, qui mesure le nombre de positions différentes entre deux chaînes de caractères. La complexité de cet algorithme est O(n), où n représente la longueur des positions à comparer. Cette complexité est linéaire, car chaque bit des hashages doit être comparé individuellement. Bien que cet algorithme soit optimal pour des comparaisons simples et directes de hashages, il peut ne pas être le plus efficace pour des bases de données volumineuses, où des techniques d'indexation ou des algorithmes plus avancés, comme le hachage perceptuel (pHash), pourraient offrir de meilleures performances.
L'automatisation du scan et de la comparaison des hashages est réalisée en continu ou à intervalles réguliers pour analyser les images soumises par les utilisateurs et les comparer avec les hashages stockés chez les partenaires. Ce processus utilise des algorithmes comme la distance de Hamming pour détecter les correspondances et envoyer des alertes en cas de contenu non autorisé. L’utilisation de Spring Batch facilite l’extraction des hashages des partenaires par lot, permettant de gérer de grandes quantités de données de manière efficace et fiable. Ce framework optimise le traitement des hashages en les extrayant à intervalles réguliers et en traitant les données de manière parallèle, ce qui permet de maintenir une haute performance même avec des volumes importants. Grâce à Spring Batch, le système peut effectuer ces tâches par lot sans compromettre l'intégrité des données ni la performance du système, garantissant ainsi une surveillance efficace et une détection rapide des images diffusées sans consentement.
 
- 	Démonstration 
Le premier sprint inclut également la mise en place des fonctionnalités d'authentification, permettant à l'utilisateur de se connecter avec un identifiant et un mot de passe. Des valeurs par défaut ont été ajoutées afin de faciliter l'utilisation du prototype
 ![image](https://github.com/user-attachments/assets/232ed671-670b-42ef-baae-f9427ff2bdaa)

L’utilisateur peut créer un compte en ajoutant son nom et prénom et son email
 ![image](https://github.com/user-attachments/assets/075a8585-0bfc-4714-923c-ba10df5af908)
 
Elle s’ajoute aussi la fonctionnalité d’affichage des détails d’un cas comme la description complète le titre et le PIN et l’historiques des correspondances d’un case en affichant le partenaire et le lien où se trouve la correspondance 
 ![image](https://github.com/user-attachments/assets/c1231c41-eb79-4edc-8007-be0c40ceca66)

Cet historique résulte d'un système automatisé de scan et de comparaison des empreintes des clients et des partenaires, permettant de rechercher des correspondances. En cas de correspondance, une alerte est ensuite envoyée à l'utilisateur.
![image](https://github.com/user-attachments/assets/3a049a74-ae37-4d67-844b-8946cdf406a1)




