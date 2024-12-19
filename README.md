# Identification du projet

## Nom et titre du Projet

**SecureIntimacy** : Plateforme de Protection des images privées contre leur diffusion non consensuelle.

## Brève description du projet

SecureIntimacy est une plateforme innovante dédiée à la protection des individus contre la diffusion non consensuelle de leurs images intimes. Le système repose sur la génération d'empreintes numériques uniques (hash) pour chaque image soumise, facilitant leur comparaison avec des bases de données partenaires. En cas de correspondance, l'utilisateur est immédiatement alerté et peut décider des actions à entreprendre pour protéger sa vie privée.

## Public ciblé / Clients potentiels

- **Public ciblé** : Les utilisateurs soucieux de leur vie privée et de la protection de leurs données personnelles, notamment dans les contextes de partage de contenus intimes.
- **Clients potentiels** : Des entreprises, des plateformes de médias sociaux et des services de messagerie souhaitant intégrer des mécanismes de prévention contre la diffusion non consensuelle de contenus intimes, ainsi que des organisations de protection des droits numériques. Cela inclut également les célébrités, les influenceurs et les personnalités publiques qui partagent fréquemment des contenus intimes sur les plateformes numériques.

## Démo

### Définition des exigences fonctionnelles

- **Créer un cas et générer un hash** : L'utilisateur peut soumettre une image ou une vidéo, ce qui déclenche la génération d'une empreinte numérique (hash) côté client à l’aide d’un algorithme de phash. Cet hash, unique pour chaque fichier, est ensuite associé à un cas pour faciliter son identification.
- **Lister les cases** : L'utilisateur peut consulter la liste des empreintes numériques soumises. Cette fonctionnalité permet de suivre l'historique des fichiers soumis pour une gestion efficace des contenus potentiellement sensibles.
- **Visualiser les détails d’un cas et l'historique des correspondances de hashes** : Chaque utilisateur peut consulter les détails de chaque hash, y compris l'historique des correspondances détectées avec les bases de données partenaires. Cela permet une traçabilité complète et un suivi des actions entreprises en cas de correspondance.
- **Automatiser la surveillance et l’envoi d'alertes** : Un système automatisé scanne en continu les bases de données partenaires pour rechercher des correspondances avec les hashes des utilisateurs. Si une correspondance est trouvée, une alerte est envoyée à l'utilisateur concerné.
- **Authentification sécurisée** : Un système d'authentification utilisant des JSON Web Tokens (JWT) est mis en place pour garantir que seuls les utilisateurs autorisés puissent accéder à la plateforme. Cela assure la sécurité des données et la confidentialité des actions de l'utilisateur.

Avant de commencer le développement, le backlog de développement a été rédigé dans Jira. Ce backlog contient toutes les fonctionnalités et tâches nécessaires à la mise en œuvre de la plateforme SecureIntimacy. Il permet de structurer le travail en sprints et de prioriser les différentes étapes du projet, garantissant ainsi une progression continue et une gestion efficace des ressources.

![image](https://github.com/user-attachments/assets/4921abde-da6b-48a6-83bf-0f085811e69d)

### Définition des exigences techniques

- **Scalabilité** : La plateforme doit pouvoir gérer une augmentation du nombre d'utilisateurs et de données sans perte de performance. Elle doit pouvoir évoluer horizontalement, avec l'ajout de serveurs ou de ressources en fonction de la demande. L'infrastructure cloud permettra une mise à l'échelle flexible et réactive.
- **Haute disponibilité** : La plateforme doit être déployée dans un environnement haute disponibilité (HA), avec des mécanismes de redondance pour les composants critiques, comme les bases de données et les serveurs d'authentification.
- **Sécurité des données** : Les données sensibles, y compris les empreintes numériques (hashes) et les informations des utilisateurs, doivent être stockées et transmises de manière sécurisée. Cela inclut l’utilisation du chiffrement AES pour le stockage des données et des connexions HTTPS pour sécuriser la transmission.
- **Traitement des données en temps réel** : Le système doit être capable de scanner en temps réel les bases de données partenaires pour détecter des correspondances avec les hashes des utilisateurs. Un moteur de traitement efficace et réactif doit être utilisé.
- **Performances et optimisation** : La plateforme doit garantir un faible temps de latence, notamment pour la génération des hashes et les comparaisons avec les bases de données partenaires. Des mécanismes de mise en cache et d'optimisation des requêtes doivent être utilisés pour améliorer la réactivité du système.
- **Conformité avec les normes de confidentialité** : La plateforme doit respecter les régulations de confidentialité des données, telles que le RGPD. Cela inclut la gestion des consentements utilisateurs et la possibilité de supprimer ou de modifier leurs données.
- **Mise à jour et maintenance** : Le système doit être conçu de manière modulaire pour faciliter les mises à jour régulières et la maintenance.
- **Surveillance et logs** : Des outils de surveillance doivent être mis en place pour suivre les performances de la plateforme et détecter les anomalies. Des logs détaillés des actions des utilisateurs et des systèmes doivent être collectés pour permettre un suivi complet.

### Choix techniques

![image](https://github.com/user-attachments/assets/2094dd27-5318-4476-b1ae-97c86dd83255)

### Architecture logicielle

![image](https://github.com/user-attachments/assets/e6f7d080-e8bf-436a-8b22-012502ac6da7)

## Conception et réalisation

### Premier Sprint

La figure ci-dessous illustre les différentes tâches réalisées durant le premier sprint (d'une durée de 24 jours).

#### Diagramme de UseCase

![image](https://github.com/user-attachments/assets/d24882a5-a11d-4ca6-acd3-7affd295586f)

#### Diagramme de Classe

Ci-dessous le diagramme de classe représentant les données des entités **Case**, **Hash** et **User**, nécessaires pour les premières fonctionnalités.

- **Case** : Contient un identifiant `caseNumber`, la date de création `createDate`, une description de l’image téléchargée `description`, ainsi que le titre du dossier et un PIN unique pour chaque cas.
  
![image](https://github.com/user-attachments/assets/9c16fd6a-864a-404d-8e36-33a4c673896a)

- **Hash** : Contient des informations sur le hachage généré, comme la valeur `hashValue` et la date de création `creationDate`. Le hachage est effectué côté client avec l'algorithme de Perceptual Hashing.
  
- **User** : Contient les informations concernant l'utilisateur, permettant de gérer l'affichage des cas associés.

Le **Perceptual Hashing** génère une empreinte numérique d'une image en comparant ses caractéristiques visuelles. La complexité temporelle de cette génération est O(n), où n est la taille de l'image.

#### Démonstration

SecureIntimacy se concentre sur l'amélioration de l'expérience utilisateur et de l'interface fluide. Voici des exemples d'interfaces clés de l'application :

- **Page d'Accueil**  
![image](https://github.com/user-attachments/assets/a3535225-cc39-4f16-a944-ac6b718bcfda)

- **À propos de nous**  
![image](https://github.com/user-attachments/assets/fc15cc07-fd02-4bc3-99ec-f78ebad7efd1)

- **Contactez-nous**  
![image](https://github.com/user-attachments/assets/b5f2c206-4f24-4d11-b0eb-eddeb0820c71)

- **FAQ**  
![image](https://github.com/user-attachments/assets/0d643f1c-242f-4433-8de2-c44c62ba5599)

L’utilisateur peut lister ses cas avec un titre, un extrait de description, et la date de création. Il peut aussi rechercher un cas par son nom.  
![image](https://github.com/user-attachments/assets/572a9c3f-102b-48dd-81c6-a53bbb5e2c0f)

Lors de la création d'un cas, l'utilisateur fournit un titre, une description et un PIN unique pour identifier l'image. Ensuite, l'image est ajoutée pour générer son hash. Ce hash est envoyé au backend pour être stocké.

![image](https://github.com/user-attachments/assets/458597cf-9930-4c45-a1de-c11c2e83d52b)

Une vérification est effectuée pour garantir l'unicité du hash avant chaque insertion dans la base de données.

![image](https://github.com/user-attachments/assets/8c116154-f048-4241-8281-546dac308073)

Après la création de chaque cas, l'utilisateur reçoit une notification.

![image](https://github.com/user-attachments/assets/2d0b1c98-90f8-4181-9d73-4dc011fcce59)

L’utilisateur peut également supprimer un cas, entraînant la suppression de l’empreinte et de son historique.

![image](https://github.com/user-attachments/assets/d87351ee-d770-494c-b223-cba6c28e9cde)

![image](https://github.com/user-attachments/assets/994bb6fa-7487-4c46-9acd-5f84c10b00dd)




# Deuxième Sprint

Le deuxième sprint de développement de **SecureIntimacy** a duré 25 jours et a permis de mettre en place des fonctionnalités clés liées à l’authentification, la gestion de compte, ainsi que l’automatisation du processus de scan et de comparaison des empreintes (hashes).

## b. Diagramme de UseCase général

Le diagramme de cas d'utilisation du système pour ce sprint intègre les processus d'authentification, de gestion de compte, ainsi que la détection des correspondances entre les empreintes des utilisateurs et celles stockées chez les partenaires. Il met en évidence deux acteurs principaux : 
- **Utilisateur standard** : responsable de la création de compte, de la connexion, de la réinitialisation de mot de passe, ainsi que de la gestion des cas, incluant leur création, recherche et suppression.
- **Système** : prend en charge la recherche de correspondances entre les empreintes et l'envoi d'alertes en cas de détection de contenu illicite.

![image](https://github.com/user-attachments/assets/638c2d63-27bb-4e5f-a9e3-7287c83bd0c5)

## c. Diagramme de Classe général

Le diagramme de classe montre les entités principales du système, incluant **Case**, **Hash**, **User**, mais aussi les nouvelles entités **Match** et **Partner**, ajoutées pour ce sprint. Voici une description des principales classes :
![image](https://github.com/user-attachments/assets/b8950250-170e-475e-befa-5548affa41ae)

1. **Partner** : Cette classe représente les partenaires qui partagent des bases de données de contenu protégé. Elle contient des informations telles que le nom, les coordonnées et les bases de données qu'ils fournissent. Cette classe permet de gérer l'accès aux ressources externes pour comparer les hashes et détecter les correspondances.

2. **Case** : C'est le contrôleur principal du système. Elle inclut des méthodes comme `getHistory`, qui récupère les correspondances trouvées pour un hash donné. Elle vérifie également l'unicité des cas via `isCaseExist`, empêchant la duplication de cas pour des images identiques ou similaires.

3. **Match** : Cette classe représente une correspondance entre une image téléchargée par un utilisateur et une image existante dans la base de données d'un partenaire. Elle inclut des propriétés comme `alertSent`, indiquant si une alerte a été envoyée, et `sourceLink`, l'URL où la correspondance a été trouvée. La méthode `isResentMatch()` permet de vérifier si une alerte a déjà été envoyée pour cette correspondance.

4. **User** : Elle gère les fonctionnalités liées à l'authentification et la gestion des rôles des utilisateurs.

## Algorithme de Comparaison des Hashes

La comparaison des hashages se fait à l'aide de la **distance de Hamming**, qui mesure les différences entre deux chaînes de bits. L'algorithme a une complexité **O(n)**, où **n** est la longueur des chaînes à comparer. Bien que cet algorithme soit performant pour des comparaisons simples, il peut devenir moins efficace avec de grandes bases de données. C’est pourquoi des techniques comme le **hachage perceptuel** (pHash) sont envisagées pour des performances améliorées.

## Automatisation et Traitement en Lot

L’automatisation du scan et de la comparaison des empreintes se fait à intervalles réguliers grâce à **Spring Batch**, un framework qui permet de gérer des traitements en lot de manière efficace. Ce traitement parallèle permet de maintenir une haute performance même avec de grands volumes de données, tout en garantissant l'intégrité des informations.

## d. Démonstration

Le deuxième sprint a permis de réaliser plusieurs fonctionnalités clés :

1. **Authentification** : Les utilisateurs peuvent désormais créer un compte avec leur nom, prénom et email, puis se connecter à leur compte.
   ![image](https://github.com/user-attachments/assets/c1e8fa22-09d9-4a1b-853d-325f1821fa21)


2. **Création de compte** : L'utilisateur peut ajouter son nom, prénom et email pour créer un compte sur la plateforme.

   ![image](https://github.com/user-attachments/assets/ec9af655-4758-4356-9c6d-56b360f5cfc9)


3. **Affichage des détails d'un cas** : L'utilisateur peut consulter les détails d'un cas, y compris la description complète, le titre, le PIN, ainsi que l'historique des correspondances, affichant le partenaire et le lien où la correspondance a été trouvée.

  ![image](https://github.com/user-attachments/assets/b41519b2-9c00-4152-a9c4-3d2b6d8b46cc)


4. **Envoi d'alertes** : En cas de correspondance, une alerte est envoyée à l'utilisateur, l'informant de la découverte d'une image similaire.

  ![image](https://github.com/user-attachments/assets/3c4baffc-d5d7-4b12-8c35-50bb01b28bb9)


## Conclusion

En conclusion, **SecureIntimacy** constitue une réponse puissante aux défis actuels de la protection de la vie privée sur Internet, en particulier face à la menace de la diffusion non consensuelle de contenus intimes. Grâce à la technologie du **client-side hashing**, la plateforme permet à ses utilisateurs de garder un contrôle total sur leurs données sensibles, sans avoir à les stocker sur des serveurs externes, garantissant ainsi leur confidentialité et leur sécurité.

La mise en œuvre de mécanismes de détection des images similaires, d'alertes en temps réel et d'un système d'authentification sécurisé via des **JSON Web Tokens (JWT)** renforce encore la fiabilité et l’efficacité du système. Le projet répond ainsi à un besoin urgent de solutions adaptées pour lutter contre la diffusion illicite de contenus, en offrant une expérience utilisateur fluide et intuitive, accessible même pour des personnes n’ayant pas de compétences techniques avancées.

Les prochaines étapes de **SecureIntimacy** incluront l'amélioration continue de la plateforme, l'intégration avec davantage de partenaires externes pour élargir la base de détection des contenus non autorisés, et l'optimisation des performances afin de supporter un nombre croissant d’utilisateurs. Enfin, l’objectif est d’étendre l’adoption de cette technologie à l’échelle mondiale, afin de contribuer à un environnement numérique plus sécurisé et respectueux de la vie privée de chacun.
