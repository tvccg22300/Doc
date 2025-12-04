
# Résumé des Commandes - Gestion des Utilisateurs et des Processus sous Linux

## 1. Gestion des Utilisateurs et Groupes

### Commandes de Base

| Commande      | Description                                                                                     |
|---------------|-------------------------------------------------------------------------------------------------|
| `adduser`     | Crée un utilisateur avec un répertoire personnel, un shell par défaut et des configurations minimales. |
| `useradd`     | Crée un utilisateur, nécessite des options pour le répertoire personnel et le shell.         |
| `deluser`     | Supprime un utilisateur de manière conviviale.                                               |
| `userdel`     | Supprime un utilisateur, nécessite l'option `-r` pour supprimer le répertoire personnel.     |
| `passwd`      | Modifie le mot de passe d'un utilisateur.                                                     |
| `groupadd`    | Ajoute un groupe.                                                                              |
| `groupdel`    | Supprime un groupe.                                                                           |
| `usermod`     | Modifie les propriétés d'un utilisateur (groupes, shell, etc.).                              |
| `id`          | Affiche les informations sur les identifiants utilisateur et groupe.                         |

### Exemples d'Utilisation

```bash
# Création d'un utilisateur avec adduser
adduser alf

# Création d'un utilisateur avec useradd
useradd -d /home/alf -m -g mongroup -G users,admin -u 101 alf

# Suppression d'un utilisateur avec deluser
deluser alf

# Suppression d'un utilisateur avec userdel
userdel -r alf

# Modification du mot de passe
passwd alf

# Ajout d'un groupe
groupadd -g 1001 monGroup

# Suppression d'un groupe
groupdel monAncienGroup

# Modification d'un utilisateur
usermod -a -G admin alf

# Affichage des informations utilisateur
id alf
```

## 2. Fichiers de Configuration des Utilisateurs

### Fichiers Importants

| Fichier         | Rôle                                                                                           |
|-----------------|------------------------------------------------------------------------------------------------|
| `~/.bashrc`     | Configuration du shell utilisateur, exécuté à chaque ouverture d'un terminal interactif.     |
| `~/.profile`    | Configuration du profil utilisateur, exécuté lors de la connexion.                           |
| `/etc/passwd`   | Liste des utilisateurs du système.                                                            |
| `/etc/shadow`   | Contient les mots de passe chiffrés des utilisateurs.                                         |
| `/etc/group`    | Liste des groupes du système.                                                                 |

### Commandes Associées

| Commande | Description                                                                                     |
|----------|-------------------------------------------------------------------------------------------------|
| `pwck`   | Vérifie l'intégrité des fichiers `/etc/passwd` et `/etc/shadow`.                              |

## 3. Gestion des Droits et Permissions

### Commandes de Base

| Commande | Description                                                                                     |
|----------|-------------------------------------------------------------------------------------------------|
| `chmod`  | Modifie les permissions (lecture, écriture, exécution) d'un fichier ou répertoire.          |
| `chown`  | Modifie le propriétaire d'un fichier ou répertoire.                                         |
| `sudo`   | Exécute une commande en tant qu'un autre utilisateur (par défaut root).                        |
| `su`     | Change d'utilisateur dans un terminal sans fermer la session en cours.                       |
| `su -`   | Charge complètement l'environnement de l'utilisateur cible.                                   |
| `exit`   | Reviens à l'utilisateur précédent ou ferme la session en cours.                              |
| `whoami` | Affiche l'utilisateur effectif.                                                               |
| `echo $USER` | Affiche l'utilisateur courant dans l'environnement.                                           |

### Exemples d'Utilisation

```bash
# Modification des permissions
chmod 600 /home/veilleur1/rapport.log

# Changement de propriétaire
chown veilleur2 /home/veilleur1/rapport.log

# Exécution d'une commande en tant que root
sudo apt update

# Changement d'utilisateur
su - veilleur1
```

## 4. Gestion des Processus

### Commandes de Base

| Commande      | Description                                                                                     |
|---------------|-------------------------------------------------------------------------------------------------|
| `ps`          | Liste les processus en cours d'exécution.                                                     |
| `top`         | Affiche l'activité des processus en temps réel.                                               |
| `kill`        | Envoie un signal à un processus pour le contrôler (arrêter, redémarrer, suspendre, etc.).     |
| `pkill`       | Tue tous les processus dont le nom correspond à un motif donné.                               |
| `pgrep`       | Liste les processus selon des critères spécifiques.                                           |

### Exemples d'Utilisation

```bash
# Lister les processus
ps aux

# Surveiller l'activité en temps réel
top

# Envoyer un signal à un processus
kill -9 PID

# Tuer un processus par son nom
pkill firefox-esr

# Rechercher un processus par utilisateur
pgrep -u root -l
```

## Conclusion

Ce document résume les principales commandes utilisées pour la gestion des utilisateurs, des groupes, des droits et des processus sous Linux. Ces commandes sont essentielles pour l'administration système et la sécurisation des environnements Linux.

