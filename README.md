# How Websites Work
**Date :** 29 Septembre 2025  
**Auteur :** GhostHunt3rx  
**Contact :** anonymousinconnu10@gmail.com

---

## Tâche 1 — Comment fonctionnent les sites web

### Vue d'ensemble
Quand vous visitez un site web, votre navigateur (client) envoie une **requête** à un **serveur web** qui renvoie une **réponse** contenant les données (HTML, CSS, JS, images...) que le navigateur va afficher. Un serveur web est simplement un ordinateur (physique ou virtuel) qui écoute des requêtes HTTP/HTTPS et renvoie des réponses.

### Architecture générale
Un site web se compose principalement de deux parties :
- **Front‑end (côté client)** : code exécuté dans le navigateur — HTML, CSS, JavaScript — responsable de l’affichage et de l’interaction.
- **Back‑end (côté serveur)** : application côté serveur qui traite la logique métier, la persistance (base de données), l’authentification, etc. Elle fournit les API et les pages demandées.

### Processus simplifié d’une visite
1. L’utilisateur entre une URL ou clique sur un lien.  
2. Le navigateur résout le domaine (DNS) pour obtenir une adresse IP.  
3. Le navigateur ouvre une connexion (souvent TCP → TLS si HTTPS) vers le serveur.  
4. Le navigateur envoie une requête HTTP(S).  
5. Le serveur répond avec des fichiers (HTML initial, puis CSS/JS/images).  
6. Le navigateur rend la page et exécute le JavaScript côté client.

---

## Tâche 2 — HTML

### Rôle du HTML
HTML (HyperText Markup Language) structure le contenu d’une page web : titres, paragraphes, images, liens, formulaires, etc.

### Exemple minimal d’un document HTML5
```html
<!DOCTYPE html>
<html lang="fr">
  <head>
    <meta charset="utf-8" />
    <title>Exemple</title>
  </head>
  <body>
    <h1>Bonjour le Monde</h1>
    <p>Ceci est un paragraphe.</p>
    <img src="img/cat.jpg" alt="Chat mignon" />
  </body>
</html>


## Tâche 3 — JavaScript

JavaScript (JS) rend les pages interactives et dynamiques.

### Concepts clés
- Contrôle des éléments HTML (DOM).  
- Gestion des événements (`onclick`, `onhover`, `addEventListener`).  
- Manipulation du contenu et du style.  
- Chargement inline ou via fichier externe (`<script src="..."></script>`).

### Exemple
HTML :
```html
<p id="demo">Texte initial</p>
<button id="btn">Cliquez</button>
