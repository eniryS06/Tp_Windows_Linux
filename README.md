# TP Test Windows et Linux - Administration Système


## Table des matières
- [Présentation du TP](#-présentation-du-tp)
- [Partie 1 : Virtualisation](#-partie-1--virtualisation)
- [Partie 2 : Linux](#-partie-2--linux)
- [Partie 3 : Windows](#-partie-3--windows)
- [Prérequis](#-prérequis)
- [Auteure](#-auteure)

## Présentation du TP

Ce travail pratique a pour objectif de maîtriser les concepts fondamentaux de la virtualisation et de l'administration des systèmes d'exploitation **Windows** et **Linux**. À travers ce TP, j'ai appris à :

- Créer et configurer des machines virtuelles
- Gérer les utilisateurs et les groupes sous Linux
- Configurer les réseaux (NAT, Host Only)
- Administrer les permissions et les disques
- Utiliser des outils comme Putty pour la connexion à distance

---

## Partie 1 : Virtualisation

### Configuration de la machine virtuelle

J'ai créé une machine virtuelle avec les caractéristiques suivantes :

| Caractéristique | Valeur |
|-----------------|--------|
| Processeur | 1 processeur / 2 cœurs |
| RAM | 3 GB |
| Réseau | Host Only |
| Disque 1 | 50 GB |
| Disque 2 | 20 GB |
| Démarrage | Mode BIOS |

![Configuration VM](images/vm-config.png)

### Configuration réseau NAT

Le réseau NAT a été configuré sur VMware pour permettre l'accès Internet aux machines virtuelles.

![Configuration NAT](images/nat-config.png)

### Questions - Virtualisation

**1. Quel est le rôle des VMware Tools ?**  
Les VMware Tools sont un ensemble d'utilitaires qui améliorent les performances de la machine virtuelle et permettent des fonctionnalités comme le copier-coller entre l'hôte et la VM, un meilleur support graphique, et la synchronisation de l'heure.

**2. Quelle est la différence entre Bridge et NAT ?**  
- **Bridge** : La VM est connectée directement au réseau physique comme une machine indépendante, avec sa propre adresse IP.
- **NAT** : La VM partage l'adresse IP de la machine hôte pour accéder au réseau externe.

**3. Quelle est la limite au niveau de la machine physique sur le nombre de VM créée ?**  
Il n'y a pas de limite théorique, tout dépend des ressources disponibles (RAM, CPU, espace disque).

**4. Pourquoi ai-je accès à Internet en NAT sans avoir à configurer mon IP ?**  
Le NAT (Network Address Translation) distribue automatiquement les adresses IP aux machines virtuelles et translate leurs requêtes pour accéder à Internet via l'IP de l'hôte.

**5. En quoi les snapshots sont des avantages conséquents en virtualisation ?**  
Les snapshots permettent d'enregistrer l'état d'une VM à un instant T et de revenir à cet état en cas de problème, ce qui est très utile pour les tests et les expérimentations.

---

## Partie 2 : Linux

### Configuration utilisateur et groupes

- **Utilisateur créé** : syrine
- **Groupe créé** : abdelbasset
- **Dossier créé** : `/home/syrine/Tptest`

### Permissions du dossier Tptest

Le dossier Tptest a été configuré avec les droits suivants :
- **Propriétaire** : tous les droits (lecture, écriture, exécution)
- **Groupe** : lecture et exécution uniquement
- **Autres** : aucun accès

![Permissions Linux](images/linux-permissions.png)

### Configuration réseau

La VM a été passée en mode NAT avec l'adresse IP : **.100**

![Commande ip a](images/linux-ipa.png)

Test de connectivité Internet :

![Ping réussi](images/linux-ping.png)

### Connexion avec Putty

Connexion à distance réussie via Putty avec l'utilisateur "syrine" :

![Putty connecté](images/linux-putty.png)

### Questions - Linux

**1. Que font les commandes suivantes ?**

| Commande | Explication |
|----------|-------------|
| `rm [!0-9]*[a-z]` | Supprime les fichiers qui ne commencent PAS par un chiffre ET qui se terminent par une lettre minuscule |
| `cp /etc/passwd .` | Copie le fichier passwd dans le répertoire courant |
| `grep '^[^a-m]..$' /etc/passwd` | Affiche les lignes de passwd dont le premier caractère n'est pas une lettre de 'a' à 'm' et qui contiennent exactement 3 caractères |

**2. Quel est le rôle de la partition swap ?**  
La partition swap sert de mémoire virtuelle. Elle permet d'étendre la mémoire RAM disponible et d'améliorer la gestion de la mémoire système.

**3. Quelle commande permet de renommer un fichier ?**  
La commande `mv` (move) : `mv ancien_nom nouveau_nom`

**4. Dans la commande `cd ../../bin`, utilise-t-on un chemin absolu ou relatif ?**  
C'est un **chemin relatif** car il part du répertoire courant pour remonter dans l'arborescence.

---

## Partie 3 : Windows

> **Note :** La partie Windows n'a pas pu être réalisée en raison d'un problème d'ISO.

### Configuration prévue

Voici ce qui était prévu pour cette partie :

- Ajout d'un disque dur de 10 Go formaté en NTFS (lettre F:)
- Délocalisation des documents et images sur ce disque
- Exception au pare-feu pour autoriser les ping
- Création des utilisateurs Tptest1 et Tptest2
- Création du groupe EFREI
- Configuration réseau en NAT avec IP en .200

### Questions - Windows

**1. Où se situent par défaut les profils des utilisateurs sous Windows ?**  
`C:\Users\nom_utilisateur`

**2. Quel est l'équivalent du swap sous Windows ?**  
Le fichier `pagefile.sys`

**3. Peut-on installer et utiliser un Windows 10 sans interface graphique ?**  
Oui, il existe des versions Server Core ou des installations minimales, mais c'est plus rare pour Windows 10 grand public.

**4. Citez un autre type de file system autre que le NTFS pris en charge par Windows**  
- FAT32
- exFAT
- ReFS (Resilient File System)

---

## Prérequis

- **VMware Workstation** (ou VMware Player)
- **Putty** (pour la connexion SSH)
- **Image ISO** d'une distribution Linux (Ubuntu/Debian)
- **Image ISO** de Windows 10
- Connaissances de base en ligne de commande

## Structure du dépôt
     TP-Windows-Linux
├── 	README.md # Ce fichier
├── 	images/
│ ├── vm-config.png # Configuration VM
│ ├── nat-config.png # Configuration NAT
│ ├── linux-permissions.png # Permissions Linux
│ ├── linux-ipa.png # Commande ip a
│ ├── linux-ping.png # Test ping
│ ├── linux-putty.png # Connexion Putty
│ └── (autres captures...)
└── 	Rapport_TP_Windows_Linux.pdf # Rapport détaillé


## Auteure

**ABDELBASSET Syrine**  
Bachelor 1 Cybersécurité

---

