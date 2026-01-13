# Stormshield SNS : Procédures de Déploiement & Best Practices

Ce document regroupe les procédures standards d'initialisation, de durcissement et de maintenance appliquées lors du déploiement d'une appliance Stormshield (Physique ou Virtuelle).

---

## 1. Initialisation Réseau : "Casser le Bridge"
Par défaut, le Stormshield est en mode "Switch" (Bridge 10.0.0.254/8). Pour le passer en mode "Routeur" de production, j'applique la procédure suivante:

1.  **Connexion Initiale :** Accès via HTTPS sur `https://10.0.0.254/admin` (depuis l'interface IN).
2.  **Modification du Bridge :**
    * Menu : *Configuration > Réseau > Interfaces*.
    * Action : Éditer `Bridge0` et retirer les interfaces `OUT` et `DMZ` des membres du pont.
    * *Note : Conserver l'interface IN dans le bridge temporairement pour maintenir la connexion d'administration.*
3.  **Configuration WAN (OUT) :**
    * Configurer l'interface `OUT` avec l'IP Publique (ou DHCP selon le FAI).
    * Cette action transforme l'interface en Gateway.
4.  **Finalisation :**
    * Configurer l'interface `DMZ` (ex: 172.16.0.254).
    * Configurer l'interface `IN` avec l'IP de Gateway LAN (ex: 192.168.1.254).
    * Supprimer définitivement l'objet `Bridge0`.

---

## 2. Durcissement Système (Hardening)
Application des recommandations de sécurité (basées sur les guides ANSSI) pour sécuriser le "Management Plane".

### Sécurité des Accès
* **Compte Admin :** Changement immédiat du mot de passe par défaut (`admin`).
* **SSH :** Désactivé par défaut. Si activé, utilisation exclusive de **clés cryptographiques** (pas de mot de passe).
* **Restrictions IP :** Limitation de l'accès à l'interface Web d'administration (`https://.../admin`) aux seules adresses IP des administrateurs ou au VLAN de Management.
* **Port Administration :** Changement du port par défaut (443 -> ex: 4433) pour limiter les scans automatiques.

### Services Critiques
* **NTP (Temps) :** Configuration d'un serveur NTP interne ou fiable. Une horloge synchronisée est critique pour la validité des certificats et la corrélation des logs.
* **DNS :** Configuration des serveurs DNS pour permettre au firewall de résoudre les noms (nécessaire pour les mises à jour Active Update).

---

## 3. Maintenance & Cycle de Vie
Gestion des mises à jour via le mécanisme de **Double Partition** pour assurer la résilience.

### Procédure de Mise à Jour Firmware
1.  **Sauvegarde :** Export de la configuration actuelle (`.na`) chiffrée par mot de passe.
2.  **Préparation Partition :** Cocher l'option *"Sauvegarder la partition active sur la partition de sauvegarde"* avant la mise à jour. Cela clone le système stable (X) vers la partition de secours avant d'installer la nouvelle version (X+1).
3.  **Installation :** Upload du fichier `.maj` et redémarrage.
4.  **Rollback (si nécessaire) :** En cas d'échec, redémarrage sur la partition de secours contenant l'ancien système sain.

---

## 4. Disaster Recovery (Accès Secours)
Si l'interface Web est inaccessible (mauvaise config réseau), j'utilise l'accès Console (CLI) :

* **Connexion Physique :** Câble série/USB sur le port `CONSOLE`.
* **Paramètres Terminal :** 9600 bauds, 8 data bits, No parity, 1 stop bit (8N1).
* **Reset Usine (Dernier recours) :** Maintenir le bouton Reset physique pendant **10 secondes** pour restaurer la configuration d'usine.