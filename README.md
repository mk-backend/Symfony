# AlphaRetail : modernisation d'une gestion de stock avec Symfony

Projet de fin d'études (RNCP niveau 7, 2024), sur un cas d'étude simulé : moderniser une application de gestion des stocks écrite en PHP natif en la reprenant avec Symfony.

Application d'origine en PHP natif : [mk-backend/gestion-de-stock-php](https://github.com/mk-backend/gestion-de-stock-php)

## Pourquoi moderniser

L'application d'origine fonctionne, mais elle devient difficile à faire évoluer : pas de routeur, du SQL écrit à la main dans chaque fichier, pas de tests.
Symfony apporte une structure claire (contrôleurs, entités, templates), l'ORM Doctrine pour la base de données et un système de sécurité prêt à l'emploi.

## Ce qui est réalisé

- **Modèle de données** en entités Doctrine : articles, catégories, clients, fournisseurs, commandes, ventes et utilisateurs, avec leurs relations.
- **Migrations Doctrine** pour créer les tables.
- **Inscription et connexion** avec Symfony Security : mots de passe hachés, authentificateur personnalisé, option « se souvenir de moi » et déconnexion.
- **Pages en Twig et Bootstrap** : tableau de bord, articles, clients et ventes, pour l'instant sous forme de maquettes (données d'exemple).

## Prochaines étapes

- Relier les pages aux données de la base (listes, ajout, modification, suppression).
- Ajouter des tests avec PHPUnit.

## Technologies

- PHP 8.2 et Symfony 7.1
- Doctrine ORM et migrations, MySQL
- Twig et Bootstrap
- Symfony Security

## Lancer le projet en local

Prérequis : PHP 8.2, Composer, MySQL et la [CLI Symfony](https://symfony.com/download).

```bash
composer install
cp .env.example .env.local
```

Dans `.env.local`, renseigner la base MySQL, par exemple :

```
DATABASE_URL="mysql://root:root@127.0.0.1:3306/alpharetail?serverVersion=8.0&charset=utf8mb4"
```

Puis créer la base et lancer le serveur :

```bash
php bin/console doctrine:database:create
php bin/console doctrine:migrations:migrate
symfony serve
```

## Organisation du code

| Dossier | Rôle |
|---|---|
| `src/Controller` | Les contrôleurs (tableau de bord, articles, clients, ventes, inscription, connexion) |
| `src/Entity` | Les entités Doctrine (le modèle de données) |
| `src/Repository` | Les requêtes vers la base de données |
| `src/Security` | L'authentificateur personnalisé |
| `templates` | Les pages Twig |
| `migrations` | Les migrations Doctrine |
