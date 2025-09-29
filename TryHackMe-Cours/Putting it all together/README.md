# Putting it all together
**Date :** 29 Septembre 2025  
**Auteur :** GhostHunt3rx  
**Contact :** anonymousinconnu10@gmail.com

---

## Tâche 1 — Tout mettre en place

### Résumé global
Lorsque vous demandez une page web, plusieurs composants travaillent ensemble en arrière‑plan pour que le navigateur affiche correctement la page :

1. **Résolution DNS** : le nom de domaine est résolu en adresse IP du serveur.  
2. **Connexion réseau** : le navigateur ouvre une connexion TCP (puis TLS si HTTPS) vers l’IP/port du serveur.  
3. **Requête HTTP(S)** : le navigateur envoie une requête HTTP(S) (GET/POST/etc.).  
4. **Réponse serveur** : le serveur renvoie du HTML, CSS, JS, images…  
5. **Rendu client** : le navigateur parse le HTML, charge les ressources (CSS/JS), exécute le JavaScript et affiche la page.

Ces étapes sont soutenues par d’autres composants (CDN, équilibreurs de charge, bases de données, WAF) qui améliorent performance, disponibilité et sécurité.

---

## Tâche 2 — Autres composants (optimisation, résilience et sécurité)

### Équilibreurs de charge (Load Balancers)
- **Rôle** : répartir le trafic entrant entre plusieurs serveurs back‑end pour assurer montée en charge et haute disponibilité.
- **Algorithmes courants** :
  - *Round‑robin* : distribue les requêtes tour à tour.
  - *Weighted* : envoie plus de requêtes aux serveurs plus puissants.
  - *Least connections* : favorise le serveur avec le moins de connexions actives.
- **Health checks** : l’équilibreur teste périodiquement l’état des serveurs et exclut ceux qui sont défaillants jusqu’à leur rétablissement.
- **Bénéfices** : tolérance aux pannes, montée en charge horizontale, maintenance sans interruption.

### CDN (Content Delivery Network)
- **Rôle** : servir les fichiers statiques (images, CSS, JS, vidéos) depuis des serveurs proches géographiquement de l’utilisateur.
- **Fonctionnement** : quand un utilisateur demande un asset, le CDN redirige la requête vers le nœud le plus proche (latence réduite).
- **Bénéfices** : meilleure performance (latence), réduction de la charge sur les serveurs d’origine, mise en cache globale, disponibilité.

### Bases de données
- **Rôle** : stocker et fournir des données persistantes (comptes, articles, commentaires, etc.).
- **Types** :
  - *SQL* : MySQL, PostgreSQL, MSSQL (schéma structuré).  
  - *NoSQL* : MongoDB, Redis (flexibilité, performances pour certains cas).
- **Architecture** : d’un simple fichier ou instance jusqu’à des clusters répliqués et sharded pour la scalabilité et la résilience.
- **Considérations** : sauvegardes, réplication, latence, cohérence, et sécurité (auth, chiffrement).

### WAF (Web Application Firewall)
- **Rôle** : placer une protection entre la requête de l’utilisateur et le serveur web pour bloquer attaques connues (XSS, SQLi, bots, DDoS légers).
- **Fonctionnalités** :
  - Filtrage des requêtes en fonction de signatures et règles (ex. OWASP CRS).  
  - Rate limiting : limiter le nombre de requêtes par IP/intervalle.  
  - Détection de comportements anormaux (bots).  
- **Bénéfices** : baisse des risques d’exploitation de vulnérabilités, filtrage des requêtes malicieuses avant d’atteindre l’application.

---

## Tâche 3 — Fonctionnement des serveurs Web

### Qu’est‑ce qu’un serveur Web ?
- Un **serveur Web** est un logiciel qui écoute les connexions entrantes (sur un port comme 80/443) et sert du contenu via HTTP/HTTPS.
- Logiciels populaires : **Apache**, **Nginx**, **IIS**, **Node.js (serveurs applicatifs)**.

### Répertoire racine (document root)
- Le serveur sert des fichiers à partir d’un répertoire racine configuré (ex. `/var/www/html` sous Linux, `C:\inetpub\wwwroot` sous Windows).
- Exemple : la requête `http://www.example.com/picture.jpg` retourne le fichier `/var/www/html/picture.jpg` si présent.

### Hôtes virtuels (Virtual Hosts)
- Permettent d’héberger plusieurs sites (domaines) sur une seule instance de serveur.
- Le serveur lit l’en‑tête **Host** de la requête HTTP et sélectionne la configuration (répertoire racine, logs, certificats) correspondante.
- Il n’y a pas de limite pratique au nombre d’hôtes virtuels — limité par ressources et configuration.

### Contenu statique vs dynamique
- **Statique** : fichiers inchangés (images, CSS, JS, HTML statique). Servis directement par le serveur web.
- **Dynamique** : généré à la volée selon la requête (ex. pages personnalisées, résultats de recherche). Produit par le backend (PHP, Python, Node.js, etc.) après logique métier / requêtes BD.

### Langages backend / exemples
- Langages courants : **PHP**, **Python**, **Ruby**, **Node.js**, **Perl**, **Java**, etc.
- Exemple PHP simple :
  ```php
  <!-- index.php -->
  <html><body>Bonjour <?php echo htmlspecialchars($_GET["name"]); ?></body></html>
