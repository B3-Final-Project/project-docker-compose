# 🚀 MatchMe - Application de Rencontres Sociales

## 📋 Description du Projet

**MatchMe** est une application de rencontres sociales moderne inspirée des plateformes comme Tinder, développée dans le cadre du Bachelor 3 en Informatique à Ynov. L'application permet aux utilisateurs de créer des connexions amicales et romantiques à travers un système de matching intelligent et une messagerie en temps réel.

### 🎯 Fonctionnalités Principales

- **🔐 Authentification sécurisée** avec AWS Cognito
- **👤 Gestion de profils** avec photos et préférences
- **💝 Système de matching** basé sur la géolocalisation et les intérêts
- **💬 Messagerie instantanée** en temps réel avec WebSockets
- **🎁 Système de boosters** pour améliorer la visibilité
- **🛡️ Espace administrateur** pour la modération
- **📊 Tableau de bord** avec statistiques détaillées

## 🛠️ Stack Technique

### Frontend
- **Framework**: Next.js 15 avec React 19
- **Styling**: Tailwind CSS avec Radix UI
- **State Management**: TanStack Query (React Query)
- **Authentification**: AWS Cognito avec OIDC
- **Tests**: Playwright pour les tests E2E
- **Build**: Docker avec multi-stage builds

### Backend
- **Framework**: NestJS avec TypeScript
- **Base de données**: PostgreSQL avec PostGIS
- **ORM**: TypeORM avec entités relationnelles
- **API Documentation**: Swagger/OpenAPI
- **WebSockets**: Socket.io pour la messagerie temps réel
- **Authentification**: JWT avec AWS Cognito
- **Tests**: Jest pour les tests unitaires et E2E

### DevOps & Infrastructure
- **Conteneurisation**: Docker & Docker Compose
- **Cloud**: AWS (ECS, S3, CloudFront, Cognito)
- **CI/CD**: GitHub Actions
- **Monitoring**: Dozzle pour les logs
- **Sécurité**: SOPS pour le chiffrement des variables d'environnement

## 🚀 Installation et Configuration

### Prérequis

- **Node.js** (version 18 ou supérieure)
- **Git**
- **Docker** et **Docker Compose**
- **AWS CLI** (avec WSL si sur Windows)
- **SOPS** (avec WSL si sur Windows)

### 🔧 Configuration AWS

1. **Installer AWS CLI** (utiliser WSL si sur Windows)
2. **Configurer le profil AWS** en ajoutant cette configuration à votre fichier `~/.aws/config` :
   ```ini
   [profile b3]
   sso_start_url = https://d-80670b5ad9.awsapps.com/start
   sso_region = eu-west-3
   sso_account_id = 989418411786
   sso_role_name = PowerUserAccess
   region = eu-west-3
   output = json
   ```
3. **Se connecter avec votre compte AWS** :
   ```bash
   aws sso login --profile b3
   ```

### 📦 Installation

1. **Cloner le repository avec les sous-modules** :
   ```bash
   git clone --recurse-submodules https://github.com/MaxPW777/Projet-B3-Ynov.git
   cd Projet-B3-Ynov
   ```

2. **Déchiffrer les fichiers d'environnement** :
   ```bash
   npm run sops:decrypt
   ```

3. **Lancer l'application avec Docker** :
   ```bash
   # Premier lancement (build requis)
   docker compose up --build
   
   # Lancements suivants
   docker compose up
   ```

### 🌐 Accès à l'Application

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:8080
- **Documentation API**: http://localhost:8080/api/docs
- **Monitoring (Dozzle)**: http://localhost:9999

## 🏗️ Architecture du Projet

### Structure des Dossiers

```
Projet-B3-Ynov/
├── submodules/
│   ├── projet-b3-backend/          # API NestJS
│   │   ├── src/
│   │   │   ├── modules/            # Modules fonctionnels
│   │   │   ├── common/             # Entités et utilitaires partagés
│   │   │   ├── auth/               # Authentification AWS Cognito
│   │   │   └── middlewares/        # Middlewares personnalisés
│   │   └── test/                   # Tests E2E
│   └── projet-b3-frontend/         # Application Next.js
│       ├── src/
│       │   ├── app/                # Pages Next.js 13+
│       │   ├── components/         # Composants React
│       │   ├── hooks/              # Hooks personnalisés
│       │   ├── lib/                # Utilitaires et configuration
│       │   └── providers/          # Providers React
│       └── e2e/                    # Tests Playwright
├── docker-compose.yml              # Orchestration Docker
└── README.md                       # Documentation
```

### Modules Backend

- **Profile**: Gestion des profils utilisateurs
- **Matches**: Système de matching et interactions
- **Messages**: Messagerie instantanée avec WebSockets
- **Boosters**: Système de boosters pour améliorer la visibilité
- **Reports**: Signalements et modération
- **Stats**: Statistiques et analytics
- **Users**: Gestion des utilisateurs (admin)
- **Settings**: Configuration de l'application
- **Geolocate**: Services de géolocalisation
- **Seed**: Données de test et seeding

## 🔐 Sécurité

### Authentification
- **AWS Cognito** pour la gestion des utilisateurs
- **JWT** pour l'authentification des requêtes API
- **OAuth2** avec Google/Facebook (configurable)

### Protection des Données
- **Validation stricte** des entrées avec class-validator
- **Chiffrement SOPS** des variables d'environnement sensibles
- **CORS** configuré pour la sécurité cross-origin
- **Rate limiting** et protection contre les attaques

### Rôles et Permissions
- **Utilisateur standard**: Accès aux fonctionnalités de base
- **Administrateur**: Accès au back-office et modération

## 🗄️ Base de Données

### Technologies
- **PostgreSQL** avec extension **PostGIS** pour la géolocalisation
- **TypeORM** comme ORM avec entités TypeScript
- **Migrations** automatiques avec synchronisation

### Entités Principales
- **User**: Informations de base des utilisateurs
- **Profile**: Profils détaillés avec préférences
- **UserMatches**: Relations de matching
- **Message**: Messages de la messagerie
- **Conversation**: Conversations entre utilisateurs
- **BoosterPack/BoosterUsage**: Système de boosters
- **Report**: Signalements et modération

## 📡 API REST

### Documentation
- **Swagger UI** disponible sur `/api/docs`
- **OpenAPI 3.0** specification
- **Tests Postman** inclus dans la documentation

### Endpoints Principaux

#### Authentification
- `POST /api/auth/login` - Connexion utilisateur
- `POST /api/auth/register` - Inscription utilisateur

#### Profils
- `GET /api/profiles` - Liste des profils
- `GET /api/profiles/:id` - Profil spécifique
- `PUT /api/profiles/:id` - Mise à jour du profil

#### Matching
- `GET /api/matches` - Profils disponibles pour matching
- `POST /api/matches/like` - Liker un profil
- `POST /api/matches/pass` - Passer un profil

#### Messagerie
- `GET /api/messages` - Conversations
- `POST /api/messages` - Envoyer un message
- `WebSocket` - Messagerie en temps réel

#### Administration
- `GET /api/admin/users` - Gestion des utilisateurs
- `GET /api/admin/reports` - Signalements
- `GET /api/admin/stats` - Statistiques

## 🎨 Frontend

### Technologies
- **Next.js 15** avec App Router
- **React 19** avec hooks modernes
- **Tailwind CSS** pour le styling
- **Radix UI** pour les composants accessibles
- **Framer Motion** pour les animations

### Pages Principales
- **Accueil**: Landing page et connexion
- **Matching**: Interface de swipe et découverte
- **Profil**: Gestion du profil utilisateur
- **Messages**: Messagerie instantanée
- **Admin**: Back-office pour la modération

### Fonctionnalités UX
- **Design Mobile First** responsive
- **Animations fluides** avec Framer Motion
- **Accessibilité RGAA** avec Radix UI
- **États de chargement** et gestion d'erreurs
- **Notifications temps réel** avec WebSockets

## 🧪 Tests

### Backend
- **Tests unitaires** avec Jest
- **Tests E2E** avec Supertest
- **Couverture de code** configurée

### Frontend
- **Tests E2E** avec Playwright
- **Tests de navigation** et interactions utilisateur
- **Tests d'accessibilité** intégrés

### Exécution des Tests
```bash
# Backend
cd submodules/projet-b3-backend
npm run test              # Tests unitaires
npm run test:e2e          # Tests E2E
npm run test:cov          # Couverture

# Frontend
cd submodules/projet-b3-frontend
npm run test:e2e          # Tests Playwright
```

## 🚀 Déploiement

### Environnements
- **Développement**: Docker Compose local
- **Staging**: AWS ECS avec auto-scaling
- **Production**: AWS ECS avec CloudFront

### Infrastructure AWS
- **ECS Fargate** pour les conteneurs
- **RDS PostgreSQL** pour la base de données
- **S3** pour le stockage des images
- **CloudFront** pour la distribution CDN
- **Cognito** pour l'authentification
- **Route 53** pour le DNS

### CI/CD
- **GitHub Actions** pour l'automatisation
- **Déploiement automatique** sur push vers main
- **Tests automatisés** avant déploiement
- **Rollback automatique** en cas d'échec

## 📊 Monitoring et Logs

### Outils
- **Dozzle** pour la visualisation des logs Docker
- **AWS CloudWatch** pour le monitoring production
- **Health checks** sur tous les services

### Métriques
- **Performance** des API
- **Utilisation** des ressources
- **Erreurs** et exceptions
- **Trafic** utilisateur

## 📚 Documentation

### Liens Utiles
- [Documentation API](http://localhost:8080/api/docs)
- [Cahier des Charges](./cahier-des-charges.md)
- [Architecture Technique](./docs/architecture.md)
- [Guide de Déploiement](./docs/deployment.md)

**Développé avec ❤️ par l'équipe MatchMe**
