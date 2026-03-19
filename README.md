# Laboratoire d’Infrastructure Windows Server

![Windows Server](https://img.shields.io/badge/Windows%20Server-2022-blue)
![Active Directory](https://img.shields.io/badge/Active%20Directory-Domain%20Services-blue)
![Linux](https://img.shields.io/badge/Linux-Debian-red)
![Samba](https://img.shields.io/badge/File%20Sharing-Samba-orange)
![Python](https://img.shields.io/badge/Python-Flask-green)
![Projet](https://img.shields.io/badge/Type-Projet%20Homelab-purple)

---
#
![windows-server](https://github.com/user-attachments/assets/a04e70ac-44dc-4b06-846e-d937e97ae17c)

---
# Présentation du projet

Ce projet est un **laboratoire personnel d’infrastructure informatique** visant à simuler un **environnement d’entreprise** basé sur **Windows Server 2022**.

L’objectif est de pratiquer et comprendre les concepts fondamentaux de **l’administration système et réseau** en mettant en place plusieurs services essentiels utilisés dans les infrastructures professionnelles.

Le laboratoire comprend notamment :

* Déploiement d’un contrôleur de domaine Active Directory
* Configuration d’un serveur DHCP
* Gestion du DNS
* Création et gestion des utilisateurs et groupes
* Application de stratégies de groupe (GPO)
* Intégration d’un système Linux dans le domaine
* Mise en place d’un serveur de fichiers Samba
* Automatisation de l’accès aux ressources
* Installation d’un serveur web IIS

Ce projet vise à reproduire une **architecture hybride Windows / Linux**, très courante dans les infrastructures informatiques modernes.

---

# Architecture de l’infrastructure

Architecture simplifiée du laboratoire :

```
doc/images/shecma.svg```

---

# Fonctionnalités mises en place

## Active Directory

Les éléments suivants ont été configurés avec succès :

* Création du domaine
* Création des unités d’organisation (OU)
* Création des groupes de sécurité
* Gestion des comptes utilisateurs
* Authentification des utilisateurs

Les utilisateurs créés dans Active Directory ont pu se connecter :

* sur un poste **Windows**
* sur une machine **Debian Linux**

L’authentification Linux a été réalisée avec :

* Kerberos
* SSSD
* Realmd

---

## DHCP et configuration réseau

Le serveur DHCP a été installé et configuré avec succès sur Windows Server.

Les éléments configurés :

* création d’une étendue IPv4
* attribution automatique des adresses IP
* configuration DNS pour le domaine

Les postes Windows reçoivent correctement leur configuration réseau.

Cependant, le comportement du **DHCP côté Linux était parfois ambigu pendant les tests**.
J’aimerais approfondir ce point dans un environnement d’infrastructure plus réaliste.

---

## Stratégies de groupe (GPO)

Plusieurs politiques de sécurité ont été mises en place :

* politique de complexité des mots de passe
* verrouillage de compte
* restriction des clés USB
* restriction du panneau de configuration

Le **test de la politique de mot de passe a fonctionné correctement**, ce qui confirme que les GPO sont bien appliquées.

Cependant, j’aimerais avoir l’opportunité de tester ces politiques **dans un environnement réel avec plusieurs postes et plusieurs services**, afin de mieux comprendre leur comportement à grande échelle.

---

## Intégration Linux dans Active Directory

Une machine **Debian** a été intégrée avec succès dans le domaine Active Directory.

Les outils utilisés :

* realmd
* SSSD
* Kerberos

Les utilisateurs du domaine peuvent ouvrir une session sur Linux avec leurs identifiants Active Directory.

Cela démontre l’interopérabilité entre **Windows et Linux dans une infrastructure commune**.

---

## Serveur de fichiers avec Samba

Un serveur Debian a été configuré comme **serveur de fichiers** intégré à Active Directory.

Fonctionnalités mises en place :

* création d’une arborescence de dossiers
* gestion des permissions avec les ACL Linux
* partage des dossiers via Samba
* gestion des accès basée sur les groupes Active Directory

Les postes Windows peuvent accéder aux partages réseau.

Cependant, **le mappage automatique des lecteurs réseau et la gestion des permissions entre Samba et les GPO se sont révélés plus complexes que prévu**.
C’est un point que je souhaiterais approfondir davantage dans un contexte professionnel.

---

## Serveur Web IIS

Le serveur **IIS** a été installé et configuré avec succès sur Windows Server.

L’environnement web est fonctionnel et prêt à accueillir des applications.

---

# Expérience : Déploiement d’une application Flask

J’ai tenté de déployer une application **Python Flask** sur le serveur IIS.

Dépôt du projet :

👉 Lien vers l’application Flask
(à remplacer par ton lien GitHub)

Même si l’installation de IIS a été réussie, **le déploiement de l’application Flask n’a pas abouti comme je le souhaitais**.

C’est un domaine que j’aimerais améliorer car l’intégration entre :

* Windows Server
* IIS
* applications Python
* authentification Active Directory

représente un cas réel très intéressant en entreprise.

---

# Expérience : Contrôle d’accès basé sur Active Directory

J’ai également tenté de mettre en place un **contrôle d’accès à l’application web basé sur les utilisateurs Active Directory**.

L’objectif était de restreindre l’accès à l’application en fonction :

* des comptes utilisateurs AD
* des groupes de sécurité AD

Cette implémentation n’a pas été entièrement réussie, mais c’est un domaine que je serais très motivé à approfondir dans un environnement réel.

---
# Expérience : Intégration d'un agent Wazuh (Sécurité / SIEM)

Dans le cadre de l'amélioration de l'infrastructure et de l'exploration des solutions de **supervision et de sécurité**, j'ai également expérimenté l'intégration d'un **agent Wazuh**.

Wazuh est une plateforme open-source utilisée pour :

* la détection d'intrusion (HIDS)
* la surveillance de l'intégrité des fichiers (FIM)
* l'analyse des journaux système
* la supervision de la sécurité des systèmes

L'objectif de cette expérimentation était de commencer à transformer l'infrastructure en **environnement supervisé**, similaire à ce que l'on retrouve dans les **centres opérationnels de sécurité (SOC)**.

---

# Surveillance de l'intégrité des fichiers (FIM)

L'une des fonctionnalités testées est le module **File Integrity Monitoring (FIM)**.

Ce module permet de :

* surveiller les fichiers critiques du système
* détecter toute modification non autorisée
* générer des alertes en cas de changement suspect

Dans ce laboratoire, l'agent Wazuh a été testé sur un serveur Windows afin d'observer les événements liés aux modifications de fichiers système.

---

# Capture du système surveillé

Ci-dessous une capture du serveur Windows utilisé pour l'expérimentation de l'agent Wazuh.

![Serveur Windows surveillé](screenshots/server_manager_windows.png)

Cette machine constitue le **serveur principal de l'infrastructure** et héberge plusieurs services critiques :

* Active Directory
* DNS
* DHCP
* IIS

L'objectif futur serait de **superviser l'ensemble des machines du laboratoire** afin d'avoir une vision centralisée des événements de sécurité.

---

# Perspectives d'amélioration

Si l'infrastructure évolue, je souhaiterais approfondir les éléments suivants :

* déploiement d'agents Wazuh sur toutes les machines
* centralisation des logs de sécurité
* détection d'activités suspectes
* mise en place d'un mini **SOC (Security Operations Center)** pour le laboratoire
* corrélation des événements de sécurité

Cela permettrait de transformer ce laboratoire en **environnement d'expérimentation complet pour la cybersécurité et la supervision d'infrastructure**.

# Ce que ce projet m’a appris

Ce laboratoire m’a permis de développer des compétences pratiques en :

* administration Windows Server
* gestion d’Active Directory
* intégration Linux dans un domaine
* authentification Kerberos
* gestion des permissions fichiers
* configuration réseau
* dépannage d’infrastructure

Au-delà de la théorie, ce projet m’a confronté à **des problématiques réelles d’administration système**.

---

# Améliorations futures

Si j’avais accès à un laboratoire plus avancé ou à un environnement professionnel, j’aimerais approfondir les aspects suivants :

* déploiement avancé des GPO
* architecture de partage de fichiers en entreprise
* authentification Active Directory pour les applications web
* reverse proxy pour applications Python
* supervision de l’infrastructure (Zabbix / Prometheus)
* SIEM et sécurité (Wazuh) avancé
* sauvegarde automatique des serveurs
* mise en place d’un VPN

---

# Compétences démontrées

Ce projet met en évidence des compétences en :

Administration système
Windows Server
Active Directory
Gestion réseau
Administration Linux
Interopérabilité Windows/Linux
Gestion des permissions
Résolution de problèmes d’infrastructure

---

# Captures

Le dépôt contient plusieurs captures d’écran du laboratoire :

* configuration Active Directory
* configuration DHCP
* stratégies de groupe
* intégration Linux dans le domaine
* serveur Samba
* accès aux partages réseau

---

# Auteur

**Manoach HOSSOU DODO**

Passionné par l’administration système, l’infrastructure informatique et la cybersécurité.

---

# Motivation

Ce projet représente ma démarche personnelle pour **apprendre en construisant une infrastructure complète**.

Certaines parties ont très bien fonctionné, d’autres ont été plus complexes, mais chacune d’entre elles a contribué à renforcer ma compréhension des systèmes.

Je suis particulièrement motivé à **continuer à apprendre et à appliquer ces compétences dans un environnement professionnel réel**.
# windows-server-cybersecurity-lab
Ce projet présente la mise en place d’une infrastructure hybride basée sur Windows Server 2022 et Linux. Il intègre Active Directory, DNS, DHCP, GPO, l’intégration Linux au domaine, un serveur de fichiers Samba avec ACL, le mappage réseau et la supervision avec Wazuh , afin de démontrer des compétences en administration système et cybersécurité.
