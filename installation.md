# 🖥️ Installation de Windows Server 2022

## 🎯 Objectif

Installer et configurer **Windows Server 2022** dans une machine virtuelle avec **VirtualBox**, afin de préparer un environnement de laboratoire pour apprendre l'administration système, réseau et Active Directory.

---

## 🧪 Environnement

- Système : Windows Server 2022
- Virtualisation : VirtualBox
- Média d'installation : ISO Windows Server 2022

---

# 1. Création de la machine virtuelle

J'ai commencé par créer une machine virtuelle dans VirtualBox afin d'y installer Windows Server 2022.

J'ai configuré notamment :

- la mémoire RAM ;
- le stockage ;
- le processeur ;
- le média d'installation.

---

# ❌ Problème 1 — Échec du premier lancement de la VM

Lors du premier lancement de la machine virtuelle avec Windows Server 2022, la VM ne démarrait pas correctement.

### Cause

Les ressources attribuées à la machine virtuelle étaient insuffisantes : 2GB RAM, 10GO Stockage et 1 CPU.

### Solution

J'ai augmenté les ressources de la VM :

- 2GB RAM --> 6GB RAM ;
- 10GO Stockage --> 50GO Stockage;
- 1 CPU --> 4 CPU.

Après ces modifications, la machine virtuelle a pu démarrer correctement.

### 🧠 Ce que j'ai appris

Une machine virtuelle doit disposer de ressources suffisantes pour permettre au système d'exploitation de fonctionner correctement.

---

# 2. Installation de Windows Server 2022

J'ai ensuite lancé l'installation de Windows Server 2022 à partir de son image ISO.

## ❌ Problème 2 — Échec de l'installation

L'installation ne se lançait pas correctement.

### Cause

Le média d'installation et l'ordre de démarrage de la machine virtuelle n'étaient pas correctement configurés. 

### Solution

J'ai :

1. utilisé l'image **ISO** de Windows Server ;
2. vérifié que l'ISO était correctement montée dans VirtualBox ;
3. vérifié l'ordre de démarrage ;
4. configuré le démarrage afin que le disque soit correctement pris en compte.

L'installation a ensuite fonctionné.

### 🧠 Ce que j'ai appris

Cette erreur m'a permis de comprendre :

- ce qu'est une image ISO ;
- comment monter une ISO dans une VM ;
- la différence entre un disque virtuel et un média d'installation ;
- l'ordre de démarrage (*boot order*) ;
- les bases du BIOS/UEFI virtuel.

---

# 📌 Résultat

Windows Server 2022 est maintenant installé et prêt à être configuré.

