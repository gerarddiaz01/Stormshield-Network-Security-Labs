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
* *03 - Translation d'adresses (NAT/PAT) (À venir)*
* *04 - Politique de Filtrage & Application Control (À venir)*
* *05 - Infrastructure à Clés Publiques (PKI) & VPN (À venir)*

---

## 🛠️ Compétences Démontrées

* **Administration SNS :** Maîtrise de l'interface Web et des commandes CLI de secours.
* **Segmentation Réseau :** Création de zones de sécurité étanches (LAN/DMZ/WAN).
* **Gestion des Risques :** Application du principe de moindre privilège sur les flux.
* **Maintenance :** Gestion du cycle de vie des firmwares (Active/Passive partitions).

---
*Ce projet est réalisé sur un environnement de virtualisation personnel.*