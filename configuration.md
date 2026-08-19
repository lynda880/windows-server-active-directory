# ⚙️ Configuration initiale du serveur

## 🎯 Objectif

Après l'installation de Windows Server 2022, j'ai configuré le serveur afin de le préparer à l'installation et à la mise en place d'Active Directory.

---

## 1. Nom du serveur

J'ai configuré le nom de la machine afin de pouvoir l'identifier facilement dans mon environnement.

Je l'ai appelé **Server2025-OC67**

Ce nom pourra correspondre au premier Domain Controller de mon laboratoire.

---

## 2. Configuration réseau

J'ai configuré les paramètres réseau du serveur :

- adresse IP ;
- masque réseau ;
- passerelle ;
- DNS.

L'objectif était notamment d'utiliser une adresse IP statique pour le serveur.

IP : 192.168.1.10  
Masque : 255.255.255.0  
Passerelle : 192.168.1.1  
DNS : 192.168.1.10

> Les valeurs ci-dessus sont les valeurs que j'ai mises.

---

## ❌ Problème 3 — Impossible de modifier certains paramètres

Je rencontrais des difficultés pour modifier :

- l'adresse IP ;
- le nom de l'ordinateur ;
- l'heure locale.

### Cause

Mon compte ne possédait pas suffisamment de privilèges administrateur, j'avais oubliée de les ajouter sur un compte de plus j'utilisais le compte utilisateur.

### Solution

J'ai utilisé un compte disposant des droits administrateur.

Cela m'a permis de modifier correctement :

- le nom du serveur ;
- l'adresse IP ;
- la configuration réseau ;
- l'heure locale.

### 🧠 Ce que j'ai appris

Certaines opérations de configuration de Windows Server nécessitent des privilèges administrateur.

---

## 3. Pourquoi utiliser une IP statique ?

Un serveur important de l'infrastructure doit avoir une adresse IP stable.

Dans un environnement Active Directory, les autres machines doivent pouvoir retrouver facilement le Domain Controller et ses services.

Une IP qui change régulièrement pourrait provoquer des problèmes de communication et de résolution DNS ce qui peut engendrer beaucoup de problèmes dans une situation réelle.

---

## 4. Configuration de l'heure

J'ai également configuré l'heure locale du serveur.

La synchronisation de l'heure est importante dans un environnement Active Directory, notamment pour les mécanismes d'authentification. 

L'heure locale de mon serveur était régler sous "United Kingdom", ce qui n'est pas mon heure locale qui est "Paris".

---

## 🧠 Ce que j'ai appris

Cette étape m'a permis de comprendre l'importance de la configuration initiale d'un serveur :

- nom de machine ;
- IP statique ;
- masque ;
- passerelle ;
- DNS ;
- heure ;
- privilèges administrateur.

Une configuration correcte du serveur est nécessaire avant de poursuivre avec Active Directory.
