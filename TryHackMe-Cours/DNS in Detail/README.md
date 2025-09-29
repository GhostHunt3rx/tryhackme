# 📘 DNS en détail  
**Date :** 29 Septembre 2025  
**Auteur :** GhostHunt3rx  
**Contact :** anonymousinconnu10@gmail.com  

---

## 🧩 Tâche 1 : Qu’est-ce que le DNS ?  
Le **DNS (Domain Name System)** agit comme un annuaire d’Internet.  
- Il traduit les **noms de domaine lisibles par l’humain** (ex. `tryhackme.com`) en **adresses IP** numériques (ex. `104.26.10.229`).  
- Objectif : faciliter la navigation en ligne sans avoir à mémoriser de longues adresses IP.

---

## 🏗️ Tâche 2 : Hiérarchie des domaines  

### 🔹 TLD (Top-Level Domain / Domaine de premier niveau)  
- Partie la plus à droite d’un domaine (`.com`, `.org`, `.fr` etc.).  
- Types :  
  - **gTLD** : génériques (ex. `.com`, `.org`, `.edu`).  
  - **ccTLD** : nationaux (ex. `.ca`, `.fr`, `.co.uk`).  

👉 Liste complète : [IANA TLDs](https://data.iana.org/TLD/tlds-alpha-by-domain.txt)  

### 🔹 Domaine de deuxième niveau  
- Partie située **avant le TLD**.  
- Exemple : `tryhackme` dans `tryhackme.com`.  
- Contraintes : max **63 caractères**, lettres/nombres/tirets (mais pas au début/fin).

### 🔹 Sous-domaine  
- Partie située **avant le domaine de deuxième niveau**.  
- Exemple : `admin` dans `admin.tryhackme.com`.  
- Possibilité d’empiler plusieurs sous-domaines (`jupiter.servers.tryhackme.com`).  
- Limite : **253 caractères maximum** pour l’ensemble du domaine.

---

## 📑 Tâche 3 : Types d’enregistrements DNS  

| Type | Description | Exemple |
|------|-------------|---------|
| **A** | Associe un domaine à une **adresse IPv4** | `104.26.10.229` |
| **AAAA** | Associe un domaine à une **adresse IPv6** | `2606:4700:20::681a:be5` |
| **CNAME** | Redirige un domaine vers un **autre nom de domaine** | `store.tryhackme.com → shops.shopify.com` |
| **MX** | Définit les serveurs qui gèrent les **e-mails** du domaine | `alt1.aspmx.l.google.com` |
| **TXT** | Contient du texte libre (vérifications, sécurité, SPF, DKIM, etc.) | Vérification domaine / anti-spam |

---

## 🔄 Tâche 4 : Processus d’une requête DNS  

1. **Cache local** : l’ordinateur vérifie s’il connaît déjà l’adresse.  
2. **Serveur DNS récursif** : souvent fourni par le FAI, interroge en cascade si nécessaire.  
3. **Serveurs racine** : orientent vers le bon TLD (.com, .org, etc.).  
4. **Serveurs TLD** : indiquent quel serveur fait autorité pour le domaine.  
5. **Serveur faisant autorité** : fournit l’enregistrement DNS exact.  
6. **Réponse finale** : renvoyée au client + mise en cache selon le **TTL (Time To Live)**.  

---

## 🛠️ Tâche 5 : Pratique  

- Des sites permettent de tester et visualiser des requêtes DNS.  
- Commandes utiles (selon OS) :  
  - **Windows** : `nslookup`  
  - **Linux/macOS** : `dig` ou `host`  

---

# ✅ Conclusion  
Le DNS est **l’épine dorsale de la navigation Internet**, transformant des noms faciles à retenir en adresses IP utilisables par les machines.  
Sa structure hiérarchique et ses différents types d’enregistrements le rendent essentiel pour :  
- la résolution de noms,  
- la gestion des sites web,  
- la sécurité des communications.  
