# Mission 1 — Le shell

**Sprint DevOps MeggieOnTheStack**  
**Promo 001 — Semaine 1 — Linux**

> À rendre avant **MARDI 4 août, 9 h 00 GMT+2**, par mail à `meggieonthestack@gmail.com`.

**Temps estimé :** 2 h à 2 h 30 de travail au total, à placer quand tu veux dans ta journée.

---

## Introduction

Hier tu as installé ta machine. Aujourd'hui tu apprends à vivre dedans.

Pas de souris, pas de fenêtres. Le clavier, c'est tout.

Cette semaine on touche 6 morceaux de Linux et le shell est le premier. Tout le reste du sprint passera par lui.

### La règle du jeu

Cette mission ne te donne pas toutes les réponses. Chercher fait partie du travail.

Le `man`, une recherche web, un essai qui rate puis un essai qui marche. C'est exactement le métier.

### La règle d'honneur

Ton compte rendu s'écrit **à la main, avec tes mots, sans IA**.

Pas ChatGPT, pas Claude, pas Gemini.

Ce que tu rends, c'est vraiment ce que **TOI** tu as fait sur **TA** machine.

Un texte généré se repère tout de suite et il ne m'intéresse pas.

Une réponse maladroite mais à toi vaut cent fois une réponse parfaite qui n'est pas la tienne.

---

# Étape 1 — La théorie

**Environ 30 minutes**

Regarde cette vidéo :

**Linux 101, commandes de base — Thomas Boutry**

https://www.youtube.com/watch?v=kG9wyUnAFI8

Puis assure-toi de pouvoir répondre à ces 4 questions.

En une phrase à toi, pas par cœur. Elles font partie du compte rendu.

1. C'est quoi un shell, et Bash c'est qui là-dedans ?
2. Il y a quoi dans `/home`, dans `/etc`, dans `/var` ?
3. Chemin absolu, chemin relatif : quelle différence ?
4. Le symbole `|` fait quoi ?

---

# Étape 2 — La pratique guidée

**Environ 30 minutes — sur TA machine**

Tout se passe dans ta VM, pas sur ton PC.

Sur Mint, ouvre l'application **Terminal**.

Sur Ubuntu Server, tu es déjà dedans depuis le login.

Déroule les 12 commandes dans l'ordre.

Lis ce que chacune te répond avant de passer à la suivante.

---

## 1. Afficher où tu te trouves

```bash
pwd
````

Permet d'afficher où tu te trouves.

C'est ton point de départ, ton dossier personnel.

---

## 2. Créer le dossier du sprint

```bash
mkdir -p sprint/semaine-1/notes
```

Permet de créer ton dossier de sprint.

L'option `-p` crée toute la chaîne de dossiers d'un coup.

---

## 3. Se déplacer dans le dossier

```bash
cd sprint/semaine-1
```

Puis :

```bash
pwd
```

Le chemin affiché a changé.

C'est ça, naviguer.

---

## 4. Créer ton premier fichier

```bash
touch notes/jour-1.txt
```

Permet de créer ton premier fichier, vide pour l'instant.

---

## 5. Écrire dans le fichier

```bash
echo "le terminal devient ma maison" > notes/jour-1.txt
```

Permet d'écrire une phrase dans le fichier.

Le signe `>` envoie le texte dans le fichier au lieu de l'écran.

---

## 6. Lire le contenu du fichier

```bash
cat notes/jour-1.txt
```

Permet de lire le contenu du fichier.

---

## 7. Copier le fichier

```bash
cp notes/jour-1.txt notes/backup.txt
```

Puis :

```bash
ls notes
```

Tu viens de copier un fichier et la liste le prouve.

---

## 8. Renommer la copie

```bash
mv notes/backup.txt notes/jour-1-backup.txt
```

`mv` déplace et renomme.

C'est la même commande.

---

## 9. Supprimer le fichier

```bash
rm notes/jour-1-backup.txt
```

Puis :

```bash
ls notes
```

Permet de vérifier la suppression.

> **Attention :** `rm` ne demande pas confirmation et il n'y a pas de corbeille.

---

## 10. Consulter le manuel

```bash
man ls
```

Permet d'ouvrir le manuel de la commande `ls`.

* On descend avec les flèches.
* On sort avec la touche `q`.

Le `man` est ta documentation officielle, sans internet.

---

## 11. Premier pipe

```bash
ls /etc | wc -l
```

Ton premier pipe.

La liste des fichiers de configuration de ta machine part dans un compteur de lignes.

Le résultat est un nombre.

---

## 12. Deuxième pipe

```bash
history | tail -5
```

Ton deuxième pipe.

Tout ton historique part dans un filtre qui n'affiche que les 5 dernières lignes.

---

## Screenshot de la pratique

Termine par un screenshot de ton terminal où l'on voit :

* le résultat de `pwd` ;
* le résultat de `ls -R ~/sprint` ;
* un de tes deux pipes.

Le screenshot part dans le compte rendu.

---

# Étape 3 — La chasse : Bandit, niveaux 0 à 5

## OBLIGATOIRE

Ce n'est pas un bonus, c'est une obligation, et c'est là que tu vas vraiment apprendre.

Personne ne te donnera la commande.

**Bandit** est un jeu de piste dans un terminal.

À chaque niveau, un mot de passe est caché quelque part et la page du niveau te dit seulement quoi chercher.

À toi de trouver comment.

### Consignes

Les consignes de chaque niveau sont ici :

[https://overthewire.org/wargames/bandit/](https://overthewire.org/wargames/bandit/)

---

## Connexion au jeu

Pour entrer dans le jeu, ouvre le terminal de ta VM et tape :

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Le mot de passe de départ est :

```text
bandit0
```

Rien ne s'affiche quand tu le tapes, c'est normal.

Valide avec **Entrée**.

Et au passage, tu viens de faire ta première connexion SSH, le pilier 6 de la semaine.

On en reparlera.

---

## Objectif

Atteindre le **niveau 5**.

Donc :

* résoudre le niveau 0 ;
* résoudre le niveau 1 ;
* résoudre le niveau 2 ;
* résoudre le niveau 3 ;
* résoudre le niveau 4 ;
* récupérer le mot de passe qui ouvre le niveau 5.

---

## Captures d'écran

À chaque niveau résolu, fais une capture d'écran où l'on voit :

* la commande qui t'a donné le mot de passe ;
* le résultat de la commande.

**Cinq captures au total, une par niveau.**

Elles partent dans ton compte rendu.

C'est ta preuve de chasse, niveau par niveau.

---

## Les règles de la chasse

### 1. Interdit

Interdit de copier une solution toute faite trouvée sur internet.

Tu te prives du seul truc qui compte : **chercher**.

### 2. Autorisé et encouragé

Tu peux utiliser :

* le `man` ;
* la page d'aide du niveau ;
* rechercher ce que fait une commande ;
* essayer ;
* rater ;
* réessayer.

### 3. Bloqué plus de 30 minutes

Poste dans `#sos-debug` ce que tu as déjà tenté.

On te donnera une piste, jamais la réponse.

### 4. Le mot de passe ne se partage pas sur le serveur

Le mot de passe ne va que dans ton mail.

---

# Étape 4 — Le compte rendu à envoyer

**Par mail à :** `meggieonthestack@gmail.com`

**Date limite :** MARDI 4 août, 9 h 00 GMT+2.

---

## Objet du mail

En objet, écris :

> Mission 1 suivi de ton pseudo Discord, TON VRAI NOM et ton pays

Cela permet de s'y retrouver avec les différences d'heures.

---

## Format du compte rendu

Écrit à la main, avec tes mots, sans IA.

Court et honnête.

**Quinze lignes de texte suffisent.**

Dedans, six choses :

### 1. Réponses aux questions de théorie

Tes réponses aux 4 questions de la théorie, une phrase chacune.

### 2. Screenshot de la pratique guidée

Ton screenshot du terminal.

### 3. Captures de la chasse Bandit

Tes 5 captures de la chasse Bandit, une par niveau résolu, avec la commande visible.

### 4. Mot de passe du niveau 5

Le mot de passe qui ouvre le niveau 5 de Bandit.

### 5. Commande découverte

La commande que tu as découverte pendant la chasse et qui t'a le plus servi.

Ajoute une phrase expliquant ce qu'elle fait.

### 6. Blocage et résolution

Explique :

* où tu as bloqué ;
* comment tu t'en es sorti ;
* une question pour le lab de mercredi si tu en as une.

---

# Si tu bloques

Direction `#sos-debug` sur le serveur, à n'importe quelle heure.

Poste ton message d'erreur **en entier**, copié-collé, pas une description.

Pour Bandit, montre ce que tu as tenté.

Tu recevras une piste, pas la réponse.

> On debug ensemble, c'est fait pour ça.

---

# Si la machine n'est pas encore installée

Tu n'as pas encore installé ta machine ?

Rien n'est perdu.

Poste ton screenshot d'installation dans `#le-lab` aujourd'hui et enchaîne sur la mission.
