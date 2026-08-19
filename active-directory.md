# 🏢 Active Directory — Notions et mise en place

## 🎯 Objectif

Cette partie présente les notions que j'ai découvertes lors de la mise en place d'Active Directory Domain Services (AD DS) ainsi que le Domain Controller (DC).

---

## 1. Active Directory

Active Directory (AD) est un service d'annuaire développé par Microsoft.

Il permet de centraliser la gestion des ressources d'un réseau Windows.

Il permet notamment de gérer :

- 👤 Utilisateurs
- 💻 Ordinateurs
- 👥 Groupes
- 📁 Unités organisationnelles (OU)
- 🔐 Permissions
- 🛡️ Politiques de sécurité
- 🌐 Machines appartenant au domaine

Sans Active Directory, chaque ordinateur peut fonctionner avec ses propres comptes locaux.

Avec Active Directory, les utilisateurs et les ordinateurs peuvent être gérés de manière centralisée.

### Exemple


                 DOMAIN CONTROLLER
                        │
                ┌───────┴────────┐
                │ Active Directory│
                └───────┬────────┘
                        │
          ┌─────────────┼─────────────┐
          │             │             │
         PC01          PC02          PC03
          │             │             │
       User01        User02        User03


---


## 2. AD DS

AD DS signifie **Active Directory Domain Services**.

Il s'agit du rôle Windows Server permettant de mettre en place un environnement Active Directory basé sur un domaine.

Il permet notamment :

- l'authentification ;
- la gestion des utilisateurs ;
- la gestion des ordinateurs ;
- la gestion des groupes ;
- la gestion des OU ;
- l'organisation du domaine ;
- l'intégration avec DNS.


---


## 3. Domain Controller (DC)

DC signifie **Domain Controller**.

Un Domain Controller est un serveur qui héberge les services nécessaires au fonctionnement d'un domaine Active Directory.

Il permet notamment :

- d'authentifier les utilisateurs ;
- d'authentifier les ordinateurs ;
- de stocker les informations Active Directory ;
- de gérer les comptes et groupes ;
- de fournir des services liés au domaine.


**Avant la promotion** : 

  Windows Server 2022 --> Serveur Classique

**Après la promotion** : 

  Windows Server 2022 --
          │
          └── Domain Controller
                  │
                  ├── Active Directory
                  ├── DNS
                  └── Domaine
                

---


## 4. Pourquoi promouvoir un serveur ?

Installer le rôle AD DS ne signifie pas automatiquement que le serveur est déjà un Domain Controller.

La promotion permet de transformer le serveur en contrôleur de domaine.


*Schéma* : 

Serveur Windows
      ↓
Installation AD DS
      ↓
Promotion du serveur
      ↓
Domain Controller
      ↓
Domaine Active Directory


Lors de la création d'un premier domaine, le serveur devient généralement le premier contrôleur de domaine de cette infrastructure.


---

## 5. Domaine Active Directory

Un domaine est une organisation logique regroupant des utilisateurs, ordinateurs et autres ressources administrées par Active Directory.

Exemple :
  entreprise.local

Dans un environnement de laboratoire :
  lab.local

Un utilisateur peut être identifié par :
  LAB\gabrielle

OU

  gabrielle@lab.local


---


## 6. AD DS vs AD CS

Il existe plusieurs services Active Directory.

| Service | Signification                                   | Fonction                                             |
| ------- | ----------------------------------------------- | ---------------------------------------------------- |
| AD DS   | Active Directory Domain Services                | Domaine, utilisateurs, ordinateurs, authentification |
| AD CS   | Active Directory Certificate Services           | Certificats numériques et PKI                        |
| AD FS   | Active Directory Federation Services            | Authentification fédérée                             |
| AD LDS  | Active Directory Lightweight Directory Services | Annuaire LDAP sans domaine Windows classique         |

Comment les reconnaîtres donc ? 

Comme ceci :

AD DS  → **Domain Services**
AD CS  → **Certificate Services**
AD FS  → **Federation Services**
AD LDS → **Lightweight Directory Services**


Dans mon projet, le rôle recherché était :
Active Directory Domain Services (AD DS)


---


## 7. Forêt, arbre et domaine

Active Directory possède plusieurs niveaux d'organisation.

*Domaine*
  Un domaine contient notamment :

lab.local
│
├── Utilisateurs
├── Ordinateurs
├── Groupes
└── OU

*Arbre — Tree*
  Un arbre peut regrouper plusieurs domaines ayant un espace de noms DNS lié.

Exemple :

  entreprise.local
  │
  ├── paris.entreprise.local
  └── lyon.entreprise.local


*Forêt — Forest*

Une forêt représente une structure Active Directory pouvant contenir plusieurs arbres et domaines.

Pour un petit laboratoire, une seule forêt et un seul domaine sont généralement suffisants.


---


## 8. OU — Organizational Unit

OU signifie Organizational Unit.

Une OU permet d'organiser les objets Active Directory.

Exemple :

lab.local
│
├── OU=Users
│   ├── Alice
│   └── Gabrielle
│
├── OU=Computers
│   ├── PC01
│   └── PC02
│
└── OU=Servers
    └── DC01

Les OU sont également importantes pour l'application des GPO.


---


## 9. Utilisateur Active Directory

Un utilisateur AD est un compte centralisé dans Active Directory.

Exemple :

  Nom   : Gabrielle
  Login : gabrielle


Connexion :

  LAB\gabrielle

OU/EGALEMENT :

  gabrielle@lab.local

Un utilisateur peut être placé dans une OU et appartenir à plusieurs groupes.


---


## 10. Groupes Active Directory

Un groupe permet de regrouper plusieurs utilisateurs ou ordinateurs.

Exemple :
  IT-Admins
  │
  ├── Alice
  ├── Gabrielle
  └── Charlie

Les groupes permettent notamment de simplifier la gestion des permissions.

Au lieu d'attribuer une permission à chaque utilisateur individuellement, elle peut être attribuée au groupe.

*Egalement, j'ai créer 3 groupes appelés : Départements Finances, Départements Ventes et Départements IT Admins.*


---


## 11. OU et groupe : différence

Il est important de ne pas confondre les deux.

OU :
  **Organisation des objets et application de certaines stratégies.**

Groupe :
  **Regroupement d'utilisateurs ou d'ordinateurs, notamment pour gérer les permissions.**

À retenir :
  OU     → Organisation
  Groupe → Regroupement / permissions


---


## 12. Ordinateur membre du domaine

Un ordinateur Windows peut être ajouté au domaine.

Avant :

  PC01
  └── Compte local

Après : 

  LAB
  │
  ├── PC01
  ├── PC02
  └── PC03

Un utilisateur du domaine peut alors se connecter avec son compte :
  **LAB\gabrielle**


---


## 13. DNS

DNS signifie Domain Name System.

Le DNS permet notamment de faire correspondre des noms avec des adresses IP.

Exemple :

server.lab.local
        ↓
192.168.1.10

Le DNS est **essentiel** au fonctionnement d'Active Directory. /!\

Les machines doivent notamment pouvoir retrouver les services du domaine.


---


14. GPO

GPO signifie Group Policy Object.

Une GPO permet d'appliquer automatiquement des paramètres aux utilisateurs et aux ordinateurs.

Exemples :

- paramètres de sécurité ;
- restrictions Windows ;
- configuration du système ;
- politiques de mot de passe.

Les GPO peuvent notamment être liées à des OU.


---


## 15. LDAP

LDAP signifie Lightweight Directory Access Protocol.

LDAP est un protocole permettant notamment d'interagir avec un annuaire.

Active Directory utilise LDAP pour certaines opérations liées à son annuaire.

/!\ **À retenir** :

Active Directory → Annuaire
LDAP             → Protocole utilisé pour communiquer avec un annuaire


---


## 16. Kerberos

Kerberos est un protocole d'authentification utilisé par Active Directory.

Il permet notamment d'authentifier les utilisateurs et de leur permettre d'accéder aux ressources auxquelles ils ont droit.


---


## 17. SID

SID signifie **Security Identifier**.

Le SID est un identifiant de sécurité attribué aux comptes et groupes Windows.

Il permet au système de distinguer les différents comptes.

Exemple :

Alice
SID → S-1-5-21-...


---


## 18. UPN

UPN signifie User Principal Name.

L'UPN permet d'identifier un utilisateur sous la forme :

  alice@lab.local

Il peut être utilisé pour la connexion à un environnement Active Directory.

---

# /!\ A noter que j'ai fais tout ceci sur l'espace de 8 mois (2025 - 2026) mais je n'avais pas documenter sur GitHub ma progression, seulement sur papier. Ce pourquoi, mes notations peuvent être maladroits. /!\
