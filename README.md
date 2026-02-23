# 🛡️ Stormshield Network Security (CSNA Lab Configuration)

**Projet de déploiement et de sécurisation d'une infrastructure réseau basée sur des appliances Stormshield SNS.**

Ce dépôt documente l'intégralité de mes laboratoires techniques réalisés dans le cadre de la préparation à la certification **CSNA (Certified Stormshield Network Administrator)**.

---

## Architecture du Lab

| Composant | Rôle | Configuration |
| :--- | :--- | :--- |
| **Firewall** | Stormshield SNS (EVA) | Filtrage, NAT, IPS, VPN SSL |
| **Zone LAN** | Trust | `192.168.1.0/24` - Administration |
| **Zone DMZ** | Services Publics | `172.16.0.0/24` - Web & DNS |
| **WAN** | Untrust | Accès Internet (Simulé) |

---

## Documentation Technique (Mes Procédures)

Voici les guides d'exploitation que j'ai rédigés basés sur les meilleures pratiques de l'ANSSI et la documentation officielle :

### Initialisation & Système
* [00 - Procédures Standards de Déploiement](./00-Deployment-Standard-Procedures.md) : *Hardening initial, cassage du bridge par défaut, gestion des partitions de boot.*
* [01 - Configuration Initiale & Logs](./01-Initial-Configuration-and-Log-Management.md) : *Sécurisation du plan d'administration et stratégie de rétention des traces.*

### Architecture & Sécurité
* [02 - Gestion des Objets Réseaux](./02-Network-Objects-Management.md) : *Structuration de la base d'objets, création de services personnalisés et automatisation (Import CSV).*
* [03 - Configuration Réseau : Interfaces & Routage](./03-Network-Interfaces-and-Routing.md) : *Définition des zones (LAN/DMZ/WAN), configuration du routage statique et mise en place du Proxy DNS.*
* [04 - Translation d'adresses (NAT)](./04-Address-Translation-NAT.md) : *Configuration du Masquerading (SNAT), publication de services via BIMAP et redirection de ports (PAT).*
* [05 - Politique de Filtrage & Supervision de Sécurité](./05-Traffic-Filtering-and-Security-Monitoring.md) : *Implémentation du filtrage strict (LAN/DMZ), contrôles applicatifs (URL/GeoIP), configuration des traces et levée d'alarmes.*
* [06 - Filtrage de Contenu Web (HTTP & HTTPS)](./06-Content-Filtering-HTTP-HTTPS.md) : *Contrôle d'accès applicatif (Couche 7), stratégie de filtrage URL et inspection SSL/TLS (SNI) sans déchiffrement.*
* [07 - Authentification & Filtrage Basé sur l'Identité](./07-Authentication-and-Identity-Based-Filtering.md) : *Intégration de l'annuaire LDAP, configuration du portail captif (enrôlement), transition du filtrage IP vers le filtrage par identité (Layer 8) et délégation des droits d'administration.*

### Connectivité Distante & VPN
* [08 - Accès Distant Sécurisé (VPN SSL)](./08_VPN_SSL_Client_Access.md) : *Mise en œuvre d'un VPN SSL Client-to-Site (OpenVPN), gestion des pools d'IP virtuels, configuration du Split/Full Tunneling, authentification des nomades et filtrage strict des flux tunnelés.*

---

## 🛠️ Compétences Démontrées

* **Administration SNS :** Maîtrise de l'interface Web et des commandes CLI de secours.
* **Segmentation Réseau :** Création de zones de sécurité étanches (LAN/DMZ/WAN).
* **Gestion des Risques :** Application du principe de moindre privilège sur les flux.
* **Maintenance :** Gestion du cycle de vie des firmwares (Active/Passive partitions).

---
*Ce projet est réalisé sur un environnement de virtualisation personnel.*