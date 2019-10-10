# Laravel-Nuxt-Decoupled

Projet de démarrage pour développer une api Laravel 6.0 avec un client Nuxt.js 2.0

## Installation

**Il faut avoir npm et composer installé localement**

1) Clôner le repo 

2) Installer les dépendances pour Nuxt, dans /client exécuter :
```cmd
npm install
```

3) Installer les dépendances pour Laravel, dans /api exécuter :
```cmd
composer install
```

4) Copier le fichier .env du root vers /api

4) Démarrer Docker
```bash
docker-compose up -d --build
```

5) Exécuter les migrations pour la base de données
```bash
docker-compose exec web bash
/var/www# php artisan migrate
```

### Laravel authentification

Le guard par défaut est le guard api pour lequel le driver jwt est utilisé.

L'authentification est gérée par JSON Web Token (JWT) voir https://github.com/tymondesigns/jwt-auth

Pour la création d'utilisateurs : endpoint POST /api/register avec les paramètres : name, email, password, password_confirmation

### Nuxt configuration

Dans le fichier de configuration nuxt.config.js, la section watchers peut être mise en commentaire si Docker n'est pas exécuté sous Windows.

### Nuxt UI

Vuetify est prêt à être utilisé par Nuxt.

