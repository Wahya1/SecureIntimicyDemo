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
![image](https://github.com/user-attachments/assets/aa4925e3-b244-4aa3-a1a3-4c6158fbd6a6)
