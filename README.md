# HACKATHON-Systeme-d-authentification


# Création d'un Système d'Authentification PHP pour une Bibliothèque (Connexion, Déconnexion, Profil)

Les systèmes d'authentification sont essentiels pour tout site web dynamique. Aujourd'hui, je partage avec vous un système complet que j'ai développé pour une application de bibliothèque, comprenant :

- *index.php* → Page d'accueil avec présentation
- *login.php* → Connexion/Inscription
- *profile.php* → Profil utilisateur
- *logout.php* → Déconnexion

## Architecture du Projet


/bibliotheque
|-- index.php          # Page d'accueil
|-- login.php          # Authentification
|-- profile.php        # Espace membre
|-- logout.php         # Déconnexion
|-- config.php         # Configuration DB
|-- /uploads           # Stockage des avatars


## Fonctionnalités Clés

1. *Système d'inscription sécurisé* :
   - Validation des emails et mots de passe
   - Hachage des mots de passe avec password_hash()
   - Upload sécurisé des avatars

2. *Connexion/Déconnexion* :
   - Gestion des sessions PHP
   - Protection des routes avec session_start()

3. *Espace membre* :
   - Sidebar de navigation
   - Affichage des informations profil
   - Design responsive et élégant

## Extraits de Code

*Connexion (login.php)* :
php
if ($user && password_verify($password, $user['password'])) {
    $_SESSION['user'] = $user['id'];
    header("Location: profile.php");
}


*Inscription* :
php
$password = password_hash($password_plain, PASSWORD_DEFAULT);
$stmt = $pdo->prepare("INSERT INTO users (...) VALUES (...)");


*Protection de profile.php* :
php
session_start();
if (!isset($_SESSION['user'])) {
    header("Location: login.php");
    exit;
}


## Design Moderne

J'ai implémenté une interface attrayante avec :

- Arrière-plan animé avec des bulles de livres
- Transition fluide entre login/register
- Sidebar élégante dans l'espace membre
- Design responsive avec Bootstrap

## Sécurité

J'ai intégré plusieurs bonnes pratiques :

- Protection contre les injections SQL avec PDO
- Hachage des mots de passe
- Validation des types de fichiers uploadés
- Protection CSRF de base

## Pour Aller Plus Loin

Ce système peut être enrichi avec :

- Un système de réservation de livres
- Des rôles utilisateurs (membre/bibliothécaire)
- Un tableau de bord d'activité
- Une réinitialisation de mot de passe par email
