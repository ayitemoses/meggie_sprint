
# Résumé - Mission 2 : Les users et les permissions

## 1. Objectifs de la mission

La mission 2 permet d'apprendre comment Linux gère les utilisateurs, les groupes et les permissions, et pourquoi ces mécanismes sont importants pour la sécurité d'un serveur. 


## 2. Contenu de la mission
Retrouvez le contenu détaillé de la mission dans [voir le dossier mission-2-users](../mission-2-users/documentation/mission-2-users.md)

## 3. Résumé final: notions principales et commandes importantes

whoami                         → affiche l'utilisateur connecté
id                             → affiche l'identité et les groupes de l'utilisateur
cat /etc/shadow                → tente d'afficher le fichier des mots de passe
sudo cat /etc/shadow | head -3 → affiche les 3 premières lignes avec les privilèges root
ls -l fichier                  → affiche les permissions et informations du fichier
chmod 600 fichier              → donne tous les droits au propriétaire et aucun aux autres
chmod 644 fichier              → donne lecture/écriture au propriétaire et lecture aux autres










