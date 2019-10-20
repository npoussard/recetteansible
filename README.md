# Ansible Rôle:  Configuration de base sur serveur cible

Un rôle Ansible qui créé des utilisateurs, un groupe, autorise la connexion SSH et supprime des utilisateurs sur des serveurs RHEL/CentOS ou Debian/Ubuntu.

Si vous utilisez des connexions SSH, vous devrez fournir votre propre paire de clé. Sur le serveur nominal, créer un paire de clé publique et privée avec une commande telle que `ssh-keygen`. Copier la clé publique générée à l'emplacement des serveurs cibles dans un fichier `authorized_key`.

## Exigence

Modifier les hôtes (adresse IP) dans le fichier `hosts.txt` selon les serveurs cibles de votre infrastructure.

## Test du playbook système

Afin de déployer la configuration écrite dans votre playbook, tester la commande : 
`ansible-playbook systeme.yml -i hosts.txt`

# Ansible Rôle: MySQL

Un rôle Ansible qui installe et configure un serveur MySQL sur des serveurs RHEL/CentOS ou Debian/Ubuntu

## Exigences

Aucune exigence particulière, notez que ce rôle nécessite un accès root.

Dans un fichier `requirement.yml` à la racine de votre projet, vous devez ajouter la source à installer et notamment pour ce projet : `- src: geerlingguy.mysql`.
Dans ce répertoire Github, le fichier et la ligne sont déjà ajoutés.
Donc, l'action précédente n'ets pas à réaliser.

Récupèrer et installer le rôle MySQL de geerlingguy (https://galaxy.ansible.com/geerlingguy/mysql)
`ansible-galaxy install -r requirement.yml`

## Test du playbook MySQL

Afin de déployer la configuration MYSQL, tester la commande : 
`ansible-playbook mysql.yml -i hosts.txt`

## Vérification du test

Sur le serveur ciblé, vérifier la Base de données créée par le playbook.
Exécuter la commande `mysql -u root -p`.
Vous serez redirigé sur le moniteur de MariaDB en SHELL.
Vous pouvez vérifier la création de la base de donnée avec la commande `show databases`

# Ansible Rôle: Apache 2.x 

Un rôle Ansible qui installe et configure un serveur Apache 2.x sur des serveurs RHEL/CentOS ou Debian/Ubuntu

## Exigences

Aucune exigence particulière, notez que ce rôle nécessite un accès root.

Dans un fichier `requirement.yml` à la racine de votre projet, vous devez ajouter la source à installer et notamment pour ce projet : `- src: geerlingguy.apache`.
Dans ce répertoire Github, le fichier et la ligne sont déjà ajoutés.

Récupèrer et installer le rôle Apache de geerlingguy 
(https://galaxy.ansible.com/geerlingguy/apache)
`ansible-galaxy install -r requirement.yml`

## Test du playbook Apache

Afin de déployer la configuration Apache, tester la commande : `ansible-playbook apache.yml -i hosts.txt`

## Vérification du test

Ajout de l'adresse IP du serveur ciblé Apache dans le fichier hosts du System32 de notre machine Windows (C:\Windows\System32\drivers\etc). Ce fichier est à ouvrir en Administrateur.

Tester l'adresse IP et le numéro de port sur un navigateur web (IE)
(http://adresse IP du serveur:80)
