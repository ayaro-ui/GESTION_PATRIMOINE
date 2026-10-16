# 🏢 GESTION_PATRIMOINE

**Application web de gestion du patrimoine et des inventaires**

GESTION_PATRIMOINE est une application web conçue pour faciliter la gestion, le suivi et l'organisation du patrimoine matériel d'un établissement. Elle permet de centraliser les informations relatives aux articles, aux stocks, aux affectations et aux mouvements, tout en améliorant la traçabilité des opérations.

Le projet repose sur Laravel et Filament pour proposer une interface d'administration structurée, PostgreSQL pour le stockage des données et un système de gestion des rôles pour contrôler les accès selon les responsabilités des utilisateurs.

## 🎯 Objectifs du projet

- Centraliser les informations relatives au patrimoine et aux articles.
- Faciliter le suivi des quantités disponibles, utilisées et neuves.
- Gérer les affectations des articles aux différents espaces et services.
- Assurer la traçabilité des mouvements et de l'historique des opérations.
- Détecter les situations nécessitant une intervention grâce aux alertes.
- Sécuriser l'accès aux fonctionnalités selon le rôle de chaque utilisateur.
- Simplifier la consultation et l'administration des données.

## 🧰 Technologies utilisées

| Technologie | Rôle |
|---|---|
| PHP 8.3 | Langage de programmation côté serveur |
| Laravel 12 | Framework backend et logique métier |
| Filament 4 | Interface d'administration |
| PostgreSQL 14 | Système de gestion de base de données |
| Tailwind CSS | Mise en forme de l'interface |
| Spatie Laravel Permission | Gestion des rôles et des permissions |
| Laravel Fortify | Fonctionnalités d'authentification |
| Laravel Sail | Environnement de développement avec Docker |
| WSL 2 / Ubuntu | Environnement Linux sous Windows |
| Docker | Conteneurisation de l'application |
| Redis | Mise en cache, selon la configuration |
| DOMPDF | Génération de documents PDF |
| Laravel Excel | Export et traitement de fichiers Excel |
| Mail / SMTP | Envoi de notifications par e-mail |
| Twilio | Envoi de notifications SMS |

## ✨ Fonctionnalités principales

### 📦 Gestion des articles et du patrimoine
- Création, consultation, modification et suppression des articles.
- Suivi des quantités totales, neuves et utilisées.
- Consultation des informations relatives à l'état et à la durée de vie des articles.
- Organisation du patrimoine par catégories et emplacements.

### 📍 Gestion des emplacements
- Organisation des articles par bâtiment, salle ou espace.
- Suivi des affectations aux différents emplacements.
- Consultation de la répartition du patrimoine dans l'établissement.

### 🔄 Gestion des affectations et des mouvements
- Affectation des articles aux emplacements concernés.
- Enregistrement des mouvements et consultation de leur historique.
- Gestion des retours en stock et des réaffectations.
- Prise en compte de l'état des articles lors des affectations.

### 🚨 Alertes et suivi
- Détection des situations de stock faible ou épuisé.
- Signalement des articles nécessitant une maintenance ou une réforme.
- Notifications par e-mail et SMS selon la configuration de l'application.

### 📊 Tableau de bord
- Consultation des indicateurs de gestion.
- Suivi de l'état du patrimoine.
- Visualisation des informations utiles à la prise de décision.

### 🔐 Gestion des utilisateurs et des permissions
L'application prévoit différents niveaux d'accès :

- **Administrateur :** administration générale et gestion des accès.
- **Gestionnaire :** gestion du patrimoine, des articles et des opérations autorisées.
- **Utilisateur :** accès aux fonctionnalités permises par son rôle.

## 🏗️ Architecture du projet

L'application suit une architecture organisée autour de Laravel :

- **Interface utilisateur :** pages d'administration construites avec Filament et Tailwind CSS.
- **Logique métier :** contrôleurs, modèles, services et règles de gestion Laravel.
- **Persistance des données :** PostgreSQL avec les modèles Eloquent et les migrations.
- **Authentification et autorisations :** mécanismes Laravel et gestion des permissions.
- **Services complémentaires :** génération PDF, export Excel et notifications.

## 📂 Structure du projet

```text
GESTION_PATRIMOINE/
├── app/
│   ├── Models/          # Modèles de données
│   ├── Http/            # Contrôleurs et logique HTTP
│   └── Filament/        # Ressources et pages d'administration
├── bootstrap/           # Initialisation de Laravel
├── config/              # Configuration de l'application
├── database/
│   ├── migrations/      # Structure de la base de données
│   ├── seeders/         # Données initiales
│   └── factories/       # Génération de données de test
├── resources/            # Vues et ressources frontend
├── routes/               # Définition des routes
├── tests/                # Tests automatisés
├── docker-compose.yml    # Orchestration Docker, si présent
├── composer.json         # Dépendances PHP
└── README.md             # Documentation du projet
```

*La structure exacte peut varier selon l'organisation des fichiers du dépôt.*

## ⚙️ Prérequis

Avant de lancer le projet, assurez-vous de disposer de :

- Git
- PHP 8.3
- Composer
- PostgreSQL 14
- Node.js et npm
- Docker Desktop et WSL 2 si vous utilisez Laravel Sail

## 🚀 Installation et lancement

### 1. Cloner le dépôt

```bash
git clone https://github.com/ayaro-ui/GESTION_PATRIMOINE.git
cd GESTION_PATRIMOINE
```

### 2. Installer les dépendances

```bash
composer install
npm install
```

### 3. Configurer l'environnement

Copiez le fichier d'environnement :

```bash
cp .env.example .env
```

Configurez ensuite les paramètres de connexion à PostgreSQL dans `.env` :

```env
DB_CONNECTION=pgsql
DB_HOST=127.0.0.1
DB_PORT=5432
DB_DATABASE=gestion_patrimoine
DB_USERNAME=postgres
DB_PASSWORD=
```

Adaptez ces paramètres à votre environnement local. Ne publiez jamais votre véritable fichier `.env`.

### 4. Générer la clé de l'application

```bash
php artisan key:generate
```

### 5. Préparer la base de données

Créez la base `gestion_patrimoine` dans PostgreSQL, puis exécutez :

```bash
php artisan migrate
```

Si le projet fournit des seeders et que vous souhaitez charger les données initiales :

```bash
php artisan db:seed
```

### 6. Lancer l'application

Dans un premier terminal :

```bash
php artisan serve
```

Dans un deuxième terminal :

```bash
npm run dev
```

L'application Laravel est alors généralement accessible à l'adresse :

http://127.0.0.1:8000

Le panneau d'administration Filament est généralement accessible à :

http://127.0.0.1:8000/admin

Si le projet utilise Laravel Sail, suivez plutôt sa configuration Docker et les commandes définies dans le dépôt.

## 🐳 Exécution avec Docker

Si le dépôt contient une configuration Docker Compose fonctionnelle, vous pouvez lancer les services avec :

```bash
./vendor/bin/sail up -d
```

Pour consulter les conteneurs actifs :

```bash
docker compose ps
```

Pour arrêter l'environnement :

```bash
./vendor/bin/sail down
```

Les commandes exactes dépendent des services et des fichiers Docker présents dans le projet.

## 🧪 Tests

Pour exécuter les tests automatisés :

```bash
php artisan test
```

Assurez-vous que l'environnement de test et la base de données sont correctement configurés avant de lancer les tests.

## 🔒 Sécurité

- Les accès sont contrôlés selon les rôles et permissions.
- Les identifiants et clés de services doivent rester dans les variables d'environnement.
- Les opérations sensibles doivent être protégées par les autorisations appropriées.
- L'authentification à deux facteurs doit être configurée et activée conformément aux fonctionnalités présentes dans le projet.


## 📄 Licence

Projet académique. 
