# HTTP en détail
**Date :** 29 Septembre 2025  
**Auteur :** GhostHunt3rx  
**Contact :** anonymousinconnu10@gmail.com

---

## Tâche 1 — Qu'est‑ce que le protocole HTTP(S) ?

### HTTP (HyperText Transfer Protocol)
HTTP est le protocole utilisé pour demander et transférer des ressources web (HTML, images, scripts, vidéos).  
- Créé par Tim Berners‑Lee (1989‑1991).  
- Basé sur un modèle requête/réponse : le client envoie une requête et le serveur renvoie une réponse.  
- Stateless : chaque requête est indépendante.  
- Versions : HTTP/0.9, 1.0, 1.1, 2, 3 (avec TLS + QUIC pour HTTP/3).

### HTTPS (HTTP Secure)
HTTPS est HTTP sur TLS/SSL.  
- Chiffre les données échangées.  
- Vérifie l’identité du serveur (certificats).  
- Assure l’intégrité et la confidentialité des échanges.

---

## Tâche 2 — Requêtes et réponses

### URL (Uniform Resource Locator)
Une URL indique comment et où accéder à une ressource.  
Composants typiques :  
- **Schéma / Protocole** : `http`, `https`, `ftp`  
- **Utilisateur** (optionnel) : `user:pass@`  
- **Hôte** : domaine ou IP (`example.com`)  
- **Port** : 1–65535 (par défaut 80 HTTP, 443 HTTPS)  
- **Chemin** : `/index.html`  
- **Query string** : `?id=1&sort=asc`  
- **Fragment** : `#section2` (côté client)

Exemple :


# HTTP — Méthodes, Codes d'état et En-têtes

**Date :** 29 Septembre 2025  
**Auteur :** GhostHunt3rx  
**Contact :** anonymousinconnu10@gmail.com

---

## Tâche 3 — Méthodes HTTP

Les méthodes HTTP permettent au client d’indiquer l’action souhaitée sur une ressource.

| Méthode | Description | Idempotence |
|---------|-------------|-------------|
| GET     | Lire / récupérer une ressource | Oui |
| POST    | Envoyer des données / créer une ressource | Non |
| PUT     | Mettre à jour / remplacer une ressource | Oui |
| DELETE  | Supprimer une ressource | Oui |
| PATCH   | Modifier partiellement une ressource | Non |
| HEAD    | Récupérer uniquement les en-têtes | Oui |
| OPTIONS | Interroger les options disponibles pour la ressource | Oui |

**Notes :**  
- Idempotent = plusieurs requêtes identiques produisent le même effet côté serveur.  
- GET/HEAD/PUT/DELETE sont généralement idempotentes, POST/PATCH non.

---

## Tâche 4 — Codes d’état HTTP

Les codes d’état informent le client du résultat de sa requête.

### Classes principales

| Classe | Plage | Description |
|--------|-------|------------|
| 1xx    | 100-199 | Informations (ex. `100 Continue`) |
| 2xx    | 200-299 | Succès (ex. `200 OK`) |
| 3xx    | 300-399 | Redirection (ex. `301 Moved Permanently`) |
| 4xx    | 400-499 | Erreur client (ex. `404 Not Found`) |
| 5xx    | 500-599 | Erreur serveur (ex. `500 Internal Server Error`) |

### Codes courants

| Code | Signification | Exemple |
|------|---------------|---------|
| 200  | OK | Requête traitée avec succès |
| 201  | Created | Nouvelle ressource créée |
| 301  | Moved Permanently | Redirection permanente |
| 302  | Found | Redirection temporaire |
| 400  | Bad Request | Requête mal formée |
| 401  | Unauthorized | Authentification requise |
| 403  | Forbidden | Accès refusé |
| 404  | Not Found | Ressource introuvable |
| 405  | Method Not Allowed | Méthode non permise |
| 500  | Internal Server Error | Erreur serveur |
| 503  | Service Unavailable | Service indisponible |

> Ressource visuelle : [http.cat](https://http.cat) pour voir les codes d’état avec images.

---

## Tâche 5 — En-têtes HTTP (Headers)

Les en-têtes ajoutent des métadonnées aux requêtes et réponses.

### En-têtes de requête (Client → Serveur)

| En-tête | Description |
|---------|------------|
| Host | Nom du domaine demandé (indispensable en virtual hosting) |
| User-Agent | Navigateur / client utilisé |
| Accept | Types MIME acceptés (ex. text/html, application/json) |
| Accept-Encoding | Compression supportée (gzip, br, deflate) |
| Accept-Language | Langue préférée |
| Authorization | Jeton / identifiants (ex. Bearer token) |
| Cookie | Cookies envoyés au serveur |
| Content-Type | Type du corps de la requête (ex. application/json) |
| Content-Length | Taille du corps (octets) |
| Referer | URL de provenance de la requête |

### En-têtes de réponse (Serveur → Client)

| En-tête | Description |
|---------|------------|
| Content-Type | Type MIME du contenu renvoyé (ex. text/html) |
| Content-Length | Longueur du corps renvoyé |
| Content-Encoding | Compression appliquée au contenu (gzip, br) |
| Set-Cookie | Définir un cookie côté client |
| Cache-Control | Directives de cache (ex. no-cache, max-age) |
| Expires | Date d’expiration du cache |
| ETag | Identifiant de version de la ressource |
| Last-Modified | Date de dernière modification de la ressource |
| Server | Identification du serveur |
| Strict-Transport-Security (HSTS) | Force l’utilisation de HTTPS |
| Content-Security-Policy (CSP) | Politique de sécurité des scripts/styles |
| X-Frame-Options | Protection clickjacking |
| X-Content-Type-Options | Protection contre le type MIME sniffing |
| Referrer-Policy | Contrôle du référent envoyé |

---

### Notes pratiques
- Les en-têtes influencent le comportement du client et du serveur.  
- Les en-têtes comme `Content-Type`, `Set-Cookie`, `Cache-Control` sont essentiels pour la sécurité, l’authentification et le cache.  
- Les navigateurs modernes utilisent DevTools pour inspecter toutes les requêtes et réponses avec leurs en-têtes et cookies.

---

