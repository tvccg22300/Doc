# sommaire
DOC TVC: Comprendre Linux
## Logo Linux
![Logo Linux](https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS0e70Um_GwfUyo6z_VTNFr2V5ISnjaLZyB6KenB6Gh83nSeXX895YBtZ5aclKQrFYpfeM&usqp=CAU)

Depuis sa création en 1991 par Linus Torvalds, Linux s’est imposé comme un système d’exploitation incontournable, utilisé dans une grande diversité d’environnements : des serveurs aux supercalculateurs, en passant par les smartphones et objets connectés. Plus qu’un simple OS, il incarne une philosophie du logiciel libre, prônant l’ouverture, la collaboration et la transparence.

## Sommaire
- [Introduction](#introduction)
- [Bash et scripting](https://github.com/tvccg22300/Doc/blob/main/README.md#bash-et-scripting)
- [TP5 Gestion des utilisateurs et des processus(fiche)](https://github.com/tvccg22300/Doc/blob/main/tp5_Gestions%20des%20utilisateurs%20et%20des%20processus.md)
- [TP5 — Section exemple](tp5.md#section-exemple)
- [TP6 (fiche)](tp6.md)
## Introduction
Dans un monde où les attaques informatiques se multiplient, la gestion des accès et des privilèges est essentielle pour sécuriser un système d’informations (SI) . Un administrateur malveillant ou une erreur humaine peut compromettre l’intégrité du système en un instant. L’objectif de cette activité est donc d’acquérir les bases pour créer, gérer et sécuriser les comptes servant à l’identification (login) et à l’authentification (password) des usagers, comprendre la gestion des permissions et analyser les journaux d’authentification en respectant le principe du moindre privilège

## Bash et scripting
En tant que  technicien veilleur en cybersécurité, vous serez confrontés à des situations plus ou moins critiques, qu'il s'agisse de prévenir une crise, de participer à la gestion d’une crise en cours, ou de réaliser des analyses post-incident (rétro-ingénierie). Pour cela, vous allez apprendre à utiliser le scripting Bash afin d’automatiser des tâches essentielles dans ces trois phases clés de la cybersécurité.

## Logo Bash
![Logo Bash](https://blog.desdelinux.net/wp-content/uploads/2019/01/bash-logo.jpg)

# Scripting Bash en Cybersécurité

---

## Introduction

En tant que **technicien veilleur en cybersécurité**, vous serez confrontés à des situations plus ou moins critiques, qu'il s'agisse de :
- Prévenir une crise,
- Participer à la gestion d’une crise en cours,
- Réaliser des analyses post-incident (rétro-ingénierie).

Pour cela, vous allez apprendre à utiliser le **scripting Bash** afin d’automatiser des tâches essentielles dans ces trois phases clés de la cybersécurité.

---

## Qu'est-ce que Bash ?

**Bash** (acronyme de *Bourne Again Shell*) est un **interpréteur de commandes** pour les systèmes d'exploitation inspirés historiquement d’Unix, notamment **Linux** et **macOS**. Il est l'un des shells les plus populaires et les plus utilisés dans le monde de :
- L'administration système,
- Le développement,
- La cybersécurité.

### Fonctionnalités de Bash
- Exécution de commandes,
- Scripting,
- Gestion de fichiers et de répertoires,
- Manipulation de texte,
- Gestion de processus,
- Redirection et pipelines,
- Gestion de variables d’environnement,
- Utilisation de structures de contrôle.

---

## Qu'est-ce que le Scripting Bash ?

Le **scripting Bash** est l'écriture de fichiers contenant une série de commandes Bash, exécutées séquentiellement pour automatiser des tâches sur les systèmes Unix/Linux.

Il permet de gérer des opérations complexes, comme :
- La manipulation de fichiers,
- L'analyse de logs,
- La gestion des processus,
- En combinant des commandes, des variables, des conditions et des boucles.

---

## Utilisation du Scripting en Cybersécurité

En cybersécurité, vous utiliserez le scripting dans des cas concrets tels que :

### 1. En Prévention d'une Crise (Mode Proactif)

Avant qu'une crise ne survienne, les techniciens en cybersécurité doivent mettre en place des mesures pour **minimiser les risques** et **détecter les menaces potentielles**. Cela inclut :

- **Surveillance continue** : Analyser les logs système et réseau pour détecter des activités suspectes.
- **Renforcement des systèmes** : Vérifier les configurations, appliquer les correctifs de sécurité, et s'assurer que les politiques de sécurité sont respectées.
- **Simulation d'attaques** : Tester les défenses pour identifier les vulnérabilités avant qu'elles ne soient exploitées.

#### Exemples de Tâches en Scripting Bash :
- Automatiser la surveillance des logs pour détecter des tentatives de connexion échouées ou des activités suspectes.
- Vérifier les permissions des fichiers sensibles (par exemple, `/etc/passwd`, `/etc/shadow`).
- Analyser les configurations système pour s'assurer qu'elles respectent les bonnes pratiques de sécurité.

---

### 2. En Gestion de Crise (Mode Réactif)

Lorsqu'une crise survient (par exemple, une attaque par ransomware, une intrusion réseau, ou une exploitation de vulnérabilité), les techniciens doivent agir rapidement pour :

- **Identifier la source de l'attaque** : Analyser les logs système, les connexions réseau, et les processus suspects.
- **Contenir l'incident** : Isoler les systèmes compromis, bloquer les adresses IP suspectes, et désactiver les comptes utilisateurs piratés.
- **Rétablir la sécurité** : Supprimer les logiciels malveillants, appliquer des correctifs de sécurité, et restaurer les systèmes à partir de sauvegardes.

#### Exemples de Tâches en Scripting Bash :
- Automatiser l'analyse des logs pour identifier les activités suspectes.
- Créer des scripts pour bloquer des adresses IP malveillantes via `iptables`.
- Surveiller les processus en temps réel pour détecter des comportements anormaux.

---

### 3. En Rétro-Ingénierie (RE) et Forensic Informatique (Post-Incident)

Après une crise, les techniciens doivent **analyser l'incident** pour comprendre comment il s'est produit, quels systèmes ont été affectés (forensic), et comment prévenir de futurs incidents en décomposant et en analysant les logiciels/malwares pour comprendre leur fonctionnement (reverse engineering). Cela inclut :

- **Analyse des logs** : Examiner les logs système et réseau pour retracer les actions de l'attaquant.
- **Identification des vulnérabilités** : Déterminer les faiblesses qui ont été exploitées.
- **Amélioration des défenses** : Mettre à jour les configurations, les politiques de sécurité, et les outils de surveillance.

#### Exemples de Tâches en Scripting Bash :
- Extraire et analyser les logs pertinents pour retracer les actions de l'attaquant.
- Automatiser la génération de rapports d'incident pour documenter les détails de l'attaque.
- Vérifier les systèmes pour s'assurer qu'ils sont sécurisés après l'incident.

---

## Conclusion

En combinant des **compétences techniques en scripting Bash** et une **compréhension approfondie des enjeux de cybersécurité**, vous serez prêts à faire face aux défis actuels et futurs dans le domaine de la sécurité informatique.
