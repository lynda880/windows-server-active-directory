# 🛠️ Problèmes rencontrés et solutions

Cette page regroupe les problèmes rencontrés pendant la mise en place de mon environnement Windows Server / Active Directory.

L'objectif est de documenter :

- le problème ;
- la cause ;
- la solution ;
- ce que j'ai appris.


**/!\ Les notes peuvent être maladroit, tout ceci est originalement sur papier, je n'avais donc juste pas mis ma progression sur GitHub en publique.**

---

## ❌ Problème 1 — Échec du premier lancement de la VM

### Symptôme

La machine virtuelle Windows Server 2022 ne démarrait pas correctement lors du premier lancement.

### Cause

Les ressources attribuées à la VM étaient insuffisantes.

### Solution

J'ai augmenté :

- la RAM ;
- le stockage ;
- le processeur.

La machine virtuelle a ensuite pu démarrer correctement.

### 🧠 Ce que j'ai appris

Une machine virtuelle doit disposer de suffisamment de ressources pour faire fonctionner correctement son système d'exploitation.

---

## ❌ Problème 2 — Échec de l'installation de Windows Server

### Symptôme

L'installation de Windows Server 2022 ne se lançait pas correctement.

### Cause

La configuration du média d'installation et de l'ordre de démarrage n'était pas correcte.

### Solution

J'ai :

1. utilisé l'ISO de Windows Server ;
2. vérifié le montage de l'ISO dans VirtualBox ;
3. vérifié l'ordre de démarrage ;
4. configuré correctement le démarrage du disque.

### 🧠 Ce que j'ai appris

Cette erreur m'a permis de comprendre :

- le fonctionnement d'une ISO ;
- le montage d'un média d'installation ;
- la différence entre un disque virtuel et une ISO ;
- l'ordre de boot ;
- les bases du BIOS/UEFI virtuel.

---

## ❌ Problème 3 — Impossible de configurer le serveur

### Symptôme

Je rencontrais des difficultés pour modifier :

- l'adresse IP ;
- le nom du serveur ;
- l'heure locale.

### Cause

Mon compte ne possédait pas suffisamment de privilèges administrateur.

### Solution

J'ai utilisé un compte disposant des droits administrateur.

J'ai ensuite pu modifier correctement :

- le nom du serveur ;
- l'adresse IP ;
- la configuration réseau ;
- l'heure locale.

### 🧠 Ce que j'ai appris

Les droits et privilèges sont importants dans Windows Server.

Certaines modifications nécessitent des droits administrateur.

---

## ❌ Problème 4 — Mauvais rôle Active Directory sélectionné

### Symptôme

Lors de l'installation du rôle Active Directory, je n'avais pas sélectionné le service correspondant à mon objectif.

### Cause

J'avais sélectionné :

**Active Directory Certificate Services (AD CS)**

alors que je voulais mettre en place :

**Active Directory Domain Services (AD DS)**.

### Solution

J'ai sélectionné le rôle :

**Active Directory Domain Services (AD DS)**

puis poursuivi la configuration du serveur.

### 🧠 Ce que j'ai appris

Les différents rôles Active Directory ont des fonctions différentes :

AD DS  → Domaine / utilisateurs / ordinateurs
AD CS  → Certificats / PKI
AD FS  → Fédération / authentification
AD LDS → Annuaire LDAP

Il est donc **important d'identifier précisément** le rôle nécessaire avant son installation.

## 📋 Résumé

| # | Problème                                | Solution                       | Statut   |
| - | --------------------------------------- | ------------------------------ | -------- |
| 1 | VM ne démarrait pas correctement        | Augmentation des ressources    | ✅ Résolu |
| 2 | Installation Windows Server impossible  | Correction ISO + ordre de boot | ✅ Résolu |
| 3 | IP / nom / heure impossibles à modifier | Droits administrateur          | ✅ Résolu |
| 4 | Mauvais rôle Active Directory           | AD CS → AD DS                  | ✅ Résolu |
