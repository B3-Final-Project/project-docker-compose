# Cahier des charges : Application de rencontres sociales “MatchMe”

## Contexte et objectifs du projet

### Contexte

Le projet “MatchMe” s’inscrit dans le cadre d’un travail de fin d’année de Bachelor, visant à démontrer les compétences acquises en conception et développement d’applications web. L’application s’inspire des plateformes de rencontres modernes telles que Tinder, tout en intégrant une dimension amicale et sociale, au-delà de la simple rencontre amoureuse.

### Objectifs généraux
- Concevoir et développer une application de rencontres sociales accessible depuis un navigateur web (et optimisée pour mobile).
- Mettre en place un système de matching permettant à la fois des rencontres amicales et romantiques.
- Proposer une expérience utilisateur fluide (UX) comprenant l’inscription, la gestion du profil, le matching et la messagerie instantanée.
- Intégrer un espace administrateur (back-office) pour la modération des utilisateurs et le suivi de l’activité.
- Assurer la sécurité et la protection des données de chaque utilisateur grâce à des mécanismes appropriés (authentification JWT, validation des entrées, etc.).

## Périmètre fonctionnel

### Espace Utilisateur

1. Inscription et connexion sécurisée 
   Inscription via email et mot de passe ou via un système OAuth (Google, Facebook).
	Authentification basée sur JWT.
2. Création de profil 
    Les utilisateurs peuvent saisir leur nom, âge, localisation, biographie, intérêts, ainsi qu’une photo de profil.
	Possibilité de configurer des préférences de recherche (tranche d’âge, distance, intérêts communs). 
3. Système de matching
	Affichage de profils correspondant aux préférences de l’utilisateur (matching basé sur localisation, intérêts communs, etc.).
	Interactions sur les profils :
	Glisser à gauche pour ignorer.
	Glisser à droite pour indiquer un intérêt.
	Un “match” est créé lorsque deux utilisateurs s’apprécient mutuellement. 
4. Messagerie instantanée
	Les utilisateurs peuvent échanger des messages en temps réel une fois le match établi. 
5. Gestion du compte
	Modification du profil, changement de mot de passe.
	Suppression du compte (désactivation/bannissement de ses données).

### Espace Administrateur (back-office)
1. Modération des utilisateurs
	Visualisation de la liste des utilisateurs.
	Possibilité de suspendre, bannir ou modifier le profil d’un utilisateur. 
2. Modération des contenus
	Gestion des signalements (comportement inapproprié, photos offensantes).
	Suppression des profils problématiques en cas de non-respect des règles. 
3. Statistiques globales
	Tableau de bord récapitulant le nombre d’inscriptions, le taux de match, l’activité des utilisateurs, etc.

## Contraintes techniques

### Environnement de travail
#### Outils de développement :
- IDE (IntelliJ, VS Code, etc.) au choix.
- Système de contrôle de version Git (obligatoire), avec repository public (GitHub, GitLab, ou Bitbucket).
- Repository Git :
    - Doit contenir un README.md détaillant la configuration et le lancement du projet.
	- Utilisation d’un .gitignore pour exclure les fichiers sensibles (ex. : .env, node_modules).
- Langages et Frameworks :
	- Backend : Node.js/Express, Spring Boot, Django, ou équivalent.
	- Frontend : React, Angular, Vue.js, ou équivalent.
	- Lien avec compétences (CDA) :
	Bloc 1 : Installer et configurer son environnement de travail (IDE, Git, etc.).

### Architecture logicielle
- Architecture multicouche (présentation, logique métier, accès aux données) pour clarifier les rôles et responsabilités.
- API REST respectant au mieux les principes de maturité HATEOAS.
#### Organisation :
- Possibilité d’architecture monolithique, SOA ou MVC selon les besoins.
- Lien avec compétences (CDA) :
    - Bloc 2 : Définir l’architecture logicielle.
    - Bloc 2 : Analyser les besoins et maquetter une application.

### Sécurité
#### Authentification sécurisée
- Utilisation de JWT (ou OAuth2, sessions sécurisées).
- Validation stricte des entrées (backend et frontend) pour prévenir les failles (injection SQL, XSS).
### Gestion des rôles :
- Utilisateur standard.
- Administrateur (back-office).
- Lien avec compétences (CDA) :
	- Impact transversal sur le développement d’une application sécurisée (Bloc 1).

### Base de données
#### Types de BDD acceptés :
- Relationnelle (MySQL, PostgreSQL, SQLite) ou NoSQL (MongoDB, Firebase).
- Si relationnelle :
    - Diagrammes conceptuel et logique (MERISE ou équivalent).
    - Justification de la modélisation (liens entre utilisateurs, matches, messages).
- Si NoSQL :
    - Justification de la structure des collections (champs, index, etc.).
    - Lien avec compétences (CDA) :
        - *Bloc 2 : Concevoir et mettre en place une base de données relationnelle.*
        - *Bloc 2 : Développer des composants d’accès aux données SQL/NoSQL.*

### API
#### Création d’une API exposant au moins 5 endpoints majeurs :
1. Inscription/Connexion 
2. Recherche/Affichage de profils 
3. Création de match 
4. Messagerie 
5. Signalement/Modération
	
#### Documentation :
- Utilisation de Swagger ou d’un outil équivalent.
- Tests :
- Tests manuels (Postman) + cahier de tests détaillé.
- Bonnes pratiques REST :
    - Verbes HTTP, statuts d’erreur, URLs claires.
    - Lien avec compétences (CDA) :
        - Bloc 3 : Préparer et exécuter les plans de tests.
        - Bloc 1 : Développer des composants métier.

### Frontend
- Maquettes préalables (Figma ou autre).
- Approche Mobile First.
- Intégration :
- Plusieurs écrans/pages fonctionnels (au moins 4) :
1. Accueil / Connexion 
2. Recherche/Matching 
3. Profil utilisateur 
4. Messagerie
- Gestion des états (chargement, erreur, succès).
- Accessibilité (conformité RGAA, tests Lighthouse, etc.).
- Lien avec compétences (CDA) :
    - Bloc 1 : Développer des interfaces utilisateur.
    - Bloc 2 : Analyser les besoins et maquetter une application.

### Hébergement
#### Hébergement de l’API et du Frontend sur des plateformes adaptées :
Heroku, Vercel, Firebase, ou autre.
Documentation des étapes d’hébergement (configurations, scripts).
Possibilité de CI/CD : pipelines d’intégration et de déploiement continu.
- Lien avec compétences (CDA) :
	- Bloc 3 : Préparer et documenter le déploiement.
	- Bloc 3 : Contribuer à la mise en production (DevOps).

### Qualité du code
#### Versioning avec Git :
- Repository public.
- Historique de commits clair (commits unitaires, messages pertinents).
- Branches de fonctionnalités.
- Fichier README.md complet (installation, configuration, exécution).
- Organisation du code :
- Respect des conventions de nommage.
- Structure de dossiers cohérente.
- Tests unitaires et fonctionnels :
- Au moins une fonctionnalité clé testée (ex. le matching).
- Lien avec compétences (CDA) :
    - Bloc 1 : Développer des composants métier.
    - Bloc 3 : Préparer et exécuter les plans de tests.
    - Bloc 3 : Contribuer à la mise en production.

### Documentation
#### Doit inclure :
- Description des choix techniques (langages, frameworks, BDD, hébergement).
- Schémas d’architecture (API + Frontend).
- Documentation des endpoints (Swagger ou Markdown).
- Captures d’écran et explications des fonctionnalités majeures.
- Lien avec compétences (CDA) :
    - Bloc 3 : Préparer et documenter le déploiement d’une application.

## Livrables attendus
### Application fonctionnelle :
Frontend + Backend déployés.
Lien d’accès à l’application.

### Code source :
Repository Git public, avec un README.md clair et un .gitignore.

### Documentation technique :
Schémas d’architecture logicielle.
Schéma de la base de données.
Document Swagger ou équivalent (endpoints).
Cahier de tests.
### Documentation utilisateur (facultative mais recommandée) :
Guide d’utilisation basique (comment s’inscrire, se connecter, etc.).
### Rapport de projet :
Justification des choix (techniques, architecturaux, etc.).
Bilans et perspectives.

## Planning et jalons
### Analyse et conception
Période : À déterminer 
Délivrables : Diagrammes (MERISE, maquettes Figma), architecture logicielle.
### Développement Backend (API)
Période : À déterminer 
Délivrables : Endpoints fonctionnels, Tests Postman, Documentation Swagger.
### Développement Frontend
Période : À déterminer 
Délivrables : Maquettes validées, pages fonctionnelles (Accueil, Matching, Profil, Messagerie).
### Intégration et tests
Période : À déterminer 
Délivrables : Tests unitaires et fonctionnels, optimisation performance, corrections de bugs.
### Hébergement et mise en production
Période : À déterminer 
Délivrables : URL finale, documentation d’hébergement, configuration CI/CD (si applicable).
### Rendu final
Période : À déterminer 
Délivrables : Projet complet et fonctionnel, documentation.
