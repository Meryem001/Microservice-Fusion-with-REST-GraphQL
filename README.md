# Microservice-Fusion-with-REST-GraphQL

L'objectif de cette activité est de s'initier au développement de microservices en utilisant Spring Boot, en mettant en œuvre un microservice dédié à la gestion de comptes bancaires. Ce microservice sera équipé de deux connecteurs, GraphQL et REST.

## Travail à faire

1. Créer un projet Spring Boot avec les dépendances Web, Spring Data JPA, H2, Lombok.
2. Créer l'entité JPA Compte.
3. Créer l'interface CompteRepository basée sur Spring Data.
4. Tester la couche DAO.
5. Créer le Web service Restfull qui permet de gérer des comptes.
6. Tester le web micro-service en utilisant un client REST comme Postman.
7. Générer et tester le documentation Swagger de des API Rest du Web service.
8. Exposer une API Restful en utilisant Spring Data Rest en exploitant des projections.
9. Créer les DTOs et Mappers.
10. Créer la couche Service (métier) et du micro service.
11. Créer un Web service GraphQL pour ce Micro-service.
Vidéos à utiliser comme ressources:
- https://www.youtube.com/watch?v=2-qIoZcvhAw 
- https://www.youtube.com/watch?v=FsdR09jlqaE

## Les dépendances utilisées 

**springdoc-openapi-ui** : Une bibliothèque qui simplifie la génération de la documentation OpenAPI (anciennement Swagger) pour vos API Spring Boot. En intégrant cette dépendance, vous obtenez une interface utilisateur interactive (UI) qui permet aux développeurs de visualiser et de tester facilement vos API. Cela facilite la compréhension et l'exploration de vos services par d'autres membres de l'équipe. <br><br>
<img width="870" alt="both" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/743a322c-91b2-433b-ae43-e7f2aadc77c1">

**spring-boot-starter-data-rest** : Cette dépendance est un starter de Spring Boot qui simplifie le développement d'API RESTful en utilisant Spring Data REST. Elle offre une solution rapide et efficace pour exposer les opérations CRUD (Create, Read, Update, Delete) sur vos entités JPA en tant que services web RESTful, tout en suivant les conventions de conception. Autrement dit, ça crée un service web générique sans avoir à créer un contrôleur REST. <br><br>
![image](https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/88d800b3-867b-4b17-8f9e-681c22489a9a)

**spring-boot-starter-graphql** : Ce starter facilite l'intégration de GraphQL dans votre application Spring Boot. GraphQL est un langage de requête flexible permettant aux clients de spécifier les données dont ils ont besoin. En ajoutant cette dépendance, vous pouvez créer des API GraphQL efficaces, permettant aux clients de demander précisément les informations souhaitées, ce qui peut améliorer les performances et l'efficacité des échanges de données entre le serveur et le client. <br><br>
![1_4WOc-E_SoW60W1uNTH8VrQ](https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/84c1d11b-f808-41a9-a5c7-3272dedc78a0)

# Micro services - First Micro service REST Connector
- Nous avons tout d'abord créé notre propre contrôleur personnalisé :
<img width="960" alt="custom" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/e51dbaab-29d5-4f86-9238-d68cdc9ab2ec">
<br><br>

- C'est possible d'importer la documentation d'une API générée par OpenAPI sur Postman afin de la tester : 
<img width="960" alt="1" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/ac428b7a-34bb-4d44-a971-d21efe1be06a">
<img width="960" alt="2" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/5617b518-8beb-4550-a32f-943e6ea4a301">
<img width="957" alt="3" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/d937d941-b5e1-499a-905c-089b3788de6c">
<br><br>

- Ensuite, nous avons exploré des fonctionnalités de Springboot Data Rest en ajoutant l'annotation ( @RepositoryRestResource ) au repository :
<img width="960" alt="rest data" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/c4efd0b4-86e3-4bab-88d4-6e188828aa6a">
<br><br>

- La pagination, la possibilité de tri, ainsi que l'inclusion des méthodes du repository JPA :
<img width="960" alt="pagination" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/39892efa-59ff-4274-b4d7-54107d7e0cf6">
<img width="960" alt="jpa methods" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/3866c808-e2c4-4621-9853-3c96a1810a80">
<br><br>

- Springboot Data Rest permet aussi de personnaliser la configuration de l'exposition des méthodes JPA en tant que point d'accès REST. Ici, la méthode sera accessible via le chemin "/byType" dans l'API REST :
<img width="960" alt="custom path and name of param" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/0432d39a-23bb-484b-9343-7d4e855df3ee">
<br><br>

- Nous utilisons des projections pour personnaliser les données que nous souhaitons obtenir :
<img width="960" alt="projection" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/5e404481-d3eb-4110-bbb4-a6ed07eb79c1">
<br>

# Micro services - First Micro service GraphQL Connector

La définition du schéma dans GraphQL est une étape cruciale, où l'on spécifie la structure et les fonctionnalités de l'API GraphQL. Ce schéma sert à définir :

1. **Types de Données** : Il peut s'agir d'objets, de scalaires, d'énumérations, d'interfaces, et d'union types. Chaque type de donnée définit les champs qui le composent.
2. **Déclaration des Champs** : Chaque champ d'un type de données est déclaré avec un nom et un type.
3. **Relations entre Types** : Vous définissez les relations entre les types à l'aide de champs spécifiques.
4. **Requêtes et Mutations** : Les requêtes définissent les opérations de lecture que les clients peuvent effectuer pour récupérer des données. Les mutations sont utilisées pour effectuer des modifications, tandis que les queries sont utilisées pour récupérer des données.
5. **Entrées** : Les entrées sont utilisées pour spécifier les arguments des mutations.
6. **Directives** : Les directives fournissent un moyen de modifier le comportement d'une requête ou d'une mutation.
7. **Validation et Documentation** : Pendant la définition du schéma, vous pouvez également spécifier des règles de validation pour garantir la cohérence et la qualité des données.
<br><br>

- Query VS Mutation : 
<img width="961" alt="query vs mutation" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/79cc4f9a-2c74-4384-9ca3-e90e684a441f">
<br><br>

- La réponse peut prendre la forme d'un objet de type (data) ou d'un objet de type (errors) : 
<img width="960" alt="retrun data vs errors" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/8f232576-5eb4-473b-a78d-a66501ce42d5">
<img width="960" alt="after exception handler" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/e114dd4e-cf09-4ba8-999c-7eebf1890851">
<br><br>

- Utilisation des parametres et variables avec les mutations : 
<img width="960" alt="mutation with params" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/54b825e9-e183-487b-8b29-9fd5730ed86a">
<br><br>

- Modification et suppression :
<img width="960" alt="update" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/dd50f85e-0925-4ed3-9d08-cca4f86a3d57">
<img width="960" alt="delete" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/e9f11274-2723-4314-9750-e1192fce80d6">
<br><br>

- GraphQL résout les problèmes liés au mapping des relations que l'on rencontre souvent avec REST :
<img width="961" alt="Screenshot 2023-12-03 160524" src="https://github.com/Ikramouslih/JEE-Activite-Pratique-2/assets/60039200/f3bfd1e2-cf59-4fd3-896e-b7c172838ab6">
<br><br>
