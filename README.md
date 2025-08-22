# 🚀 Administration de Services Réseaux sous Linux

![Statut du Projet](https://img.shields.io/badge/statut-terminé-brightgreen)
![Licence](https://img.shields.io/badge/licence-MIT-blue)

Projet académique réalisé dans le cadre du module "Interconnexion et Administration des réseaux" du Cycle d'Ingénieurs en Génie Informatique à la FST Errachidia.

Ce projet consiste en la conception, la mise en œuvre et la sécurisation d'une infrastructure réseau complète et virtualisée sous Linux, divisée en un parc informatique et un parc de recherche.

<!-- Optionnel : Ajoutez une capture d'écran de votre schéma d'architecture ici -->
![Schéma d'Architecture]([LIEN-VERS-VOTRE-CAPTURE-D-ARCHITECTURE])

---

## 🎯 Objectifs du Projet

L'objectif principal était de construire une solution réseau robuste, sécurisée et facile à administrer, en passant par trois phases majeures :

1.  **Phase 1 : Infrastructure de Base**
    *   Mise en place d'une infrastructure virtualisée avec des machines Linux.
    *   Configuration des services fondamentaux : **DNS** (Bind9) et **DHCP** (isc-dhcp-server).
    *   Déploiement d'un serveur de sauvegarde automatisé avec **Rsnapshot**.

2.  **Phase 2 : Interopérabilité et Centralisation**
    *   Centralisation de l'authentification des utilisateurs avec un serveur **NIS**.
    *   Partage de répertoires centralisé entre les machines Linux via **NFS**.
    *   Intégration de postes clients Linux et Windows dans l'infrastructure.

3.  **Phase 3 : Cybersécurité et Surveillance**
    *   Déploiement de **Security Onion**, une plateforme open-source de surveillance réseau.
    *   Configuration d'outils de détection d'intrusions (IDS) et d'analyse de menaces comme Suricata et Zeek.

---

## 🛠️ Technologies et Outils Utilisés

| Catégorie | Outils |
| :--- | :--- |
| **Système & Virtualisation** | Linux (Ubuntu Server), VirtualBox/VMware, Bash Scripting |
| **Services Réseau** | Bind9 (DNS), ISC-DHCP-Server, NFS, NIS, Rsnapshot, OpenSSH |
| **Sécurité (IDS/NSM)** | Security Onion, Suricata, Zeek, Wazuh, Kibana, Elasticsearch |
| **Clients** | Ubuntu Desktop, Windows |

---

## 🔧 Configuration Clés

Quelques exemples de configurations mises en place durant le projet.

### DHCP (`/etc/dhcp/dhcpd.conf`)
Configuration d'adresses IP fixes pour les machines critiques du réseau.
```conf
host client-linux1 {
  hardware ethernet 00:0c:29:8a:be:79;
  fixed-address 192.168.19.50;
}
host server-RSH {
  hardware ethernet 00:0c:29:08:8f:fd;
  fixed-address 192.168.19.52;
}
```

### DNS (`/etc/bind/zones/db.xx.cigi.ma`)
Fichier de zone directe pour le domaine `xx.cigi.ma`.
```dns
; A Records
ns1             IN      A       192.168.19.1
pas             IN      A       192.168.19.1
server-RSH      IN      A       192.168.19.52
client-linux1   IN      A       192.168.19.50
```

### NFS (`/etc/exports`)
Exportation d'un répertoire partagé pour le sous-réseau `192.168.229.0/24`.
```
/home/serveurnfsnis/Bureau/Partage 192.168.229.0/24(rw,sync,no_subtree_check)
```

### NIS (`/etc/default/nis`)
Configuration du serveur en tant que maître NIS pour le domaine `rd.formation.ma`.
```
NISSERVER=master
NISDOMAIN=rd.formation.ma
```

---

## 👥 Auteurs

Ce projet a été réalisé par :

*   **BANNANY Brahim** - [GitHub]([LIEN-VERS-LE-PROFIL-DE-BRAHIM])
*   **MAHROUCH Mohamed** - [GitHub](https://github.com/mohamedmahrouch)

