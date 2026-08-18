# Mission 2. Les users et les permissions

**Sprint DevOps MeggieOnTheStack. Promo 001. Semaine 1, Linux.**

> À rendre avant **mercredi 5 août, 15 h 00 GMT+2**, par mail à **[meggieonthestack@gmail.com](mailto:meggieonthestack@gmail.com)**.
> Compte **2 h à 2 h 30** de travail au total, à placer quand tu veux dans ta journée.

Hier tu as appris à vivre dans le terminal. Aujourd'hui tu apprends qui a le droit de faire quoi. C'est la base de toute la sécurité d'un serveur, et c'est là que tout le monde se plante au début. Pas toi, pas après aujourd'hui.

## La règle du jeu

Cette mission ne te donne pas toutes les réponses. Chercher fait partie du travail. Le `man`, une recherche web, un essai qui rate puis un essai qui marche. C'est exactement le métier.

## La règle d'honneur

Ton compte rendu s'écrit à la main, avec tes mots, sans IA. Pas ChatGPT, pas Claude, pas Gemini.

Ce que tu rends, c'est vraiment ce que **TOI** tu as fait sur **TA** machine. Une réponse maladroite mais à toi vaut cent fois une réponse parfaite qui n'est pas la tienne.

---

# Étape 1 — La théorie

**Environ 30 minutes**

Les vidéos du jour sont en anglais. C'est voulu. La doc, les forums et les entretiens tech parlent anglais, autant s'y mettre maintenant. Active les sous-titres si besoin, ici on est bilingues.

Regarde ces deux vidéos de **Learn Linux TV** :

* [Les permissions — Understanding File and Directory Permissions](https://www.youtube.com/watch?v=4e669hSjaX8)
* [sudo — Linux Crash Course, sudo](https://www.youtube.com/watch?v=07JOqKOBRnU)

Puis assure-toi de pouvoir répondre à ces 4 questions. En une phrase à toi, pas par cœur. Elles font partie du compte rendu.

1. **Root et un utilisateur normal, quelle différence ?**
2. **Ce que fait vraiment `sudo` quand tu le tapes ?**
3. **La ligne `rwx` d'un `ls -l`, comment on la lit ?** Propriétaire, groupe, autres.
4. **Le principe du moindre privilège, c'est quoi et pourquoi ça te protège ?**

---

# Étape 2 — La mise en jambes

**Environ 15 minutes — sur TA machine**

Six commandes pour toucher ce que les vidéos racontent. Lis ce que chacune te répond.

### 1. Voir qui tu es

```bash
whoami
id
```

Pour voir qui tu es et à quels groupes tu appartiens.

### 2. Accéder à `/etc/shadow`

```bash
cat /etc/shadow
```

Le fichier des mots de passe chiffrés. Refusé.

C'est le moindre privilège qui protège ta machine.

### 3. Utiliser sudo

```bash
sudo cat /etc/shadow | head -3
```

Même commande, pleins pouvoirs empruntés le temps d'une ligne.

La différence entre les deux essais, c'est toute la leçon du jour.

### 4. Observer les permissions

```bash
ls -l ~/sprint/semaine-1/notes/jour-1.txt
```

Lis la ligne de gauche :

* droits du propriétaire ;
* droits du groupe ;
* droits des autres.

### 5. Modifier les permissions

```bash
chmod 600 ~/sprint/semaine-1/notes/jour-1.txt
ls -l ~/sprint/semaine-1/notes/jour-1.txt
```

La ligne a changé : toi seul peux lire ce fichier désormais.

### 6. Revenir aux permissions normales

```bash
chmod 644 ~/sprint/semaine-1/notes/jour-1.txt
```

Garde un screenshot où l'on voit :

* le refus de `/etc/shadow` ;
* la version `sudo` qui passe ;
* la ligne `ls -l` avant et après ton `chmod`.

Ce screenshot part dans le compte rendu.

---

# Étape 3 — La chasse : Opération Coffre-Fort

## OBLIGATOIRE

Hier soir Bandit. Ce soir on monte d'un cran.

La chasse se passe sur **TA machine**, et elle est faite sur mesure pour la promo.

Le gardien a caché un coffre quelque part dans ta VM. Cinq indices mènent jusqu'à lui.

Chaque indice est verrouillé par un vrai mécanisme de permissions et t'oblige à un geste d'admin :

* fichiers cachés ;
* `chmod` ;
* changement d'utilisateur ;
* groupes ;
* fouille du système.

Personne ne te donnera les commandes. Les indices te disent quoi faire, à toi de trouver comment.

## Installation

Récupère le fichier `chasse-002.sh` joint au message Discord et amène-le dans ta VM.

### Sur Mint

Ouvre Discord dans le navigateur de ta VM et télécharge la pièce jointe.

### Sur Ubuntu Server

```bash
curl -L "LIEN_DU_SCRIPT" -o chasse-002.sh
```

## Avant de le lancer

Ouvre-le :

```bash
cat chasse-002.sh
```

C'est un réflexe de pro.

On ne lance jamais un script trouvé sur internet avec `sudo` sans avoir regardé ce qu'il touche.

Celui-ci crée :

* un utilisateur `gardien` ;
* un groupe `promo001` ;
* des fichiers de jeu dans deux dossiers.

Rien d'autre, et c'est écrit dedans.

Les textes sont encodés pour ne pas te spoiler la chasse.

## Lancer la chasse

```bash
sudo bash chasse-002.sh
```

Puis démarre :

```bash
cd /opt/chasse
```

Lis ensuite :

```bash
cat BIENVENUE.txt
```

Tout casser n'est pas grave : relancer le script remet la chasse à zéro.

## Les règles de la chasse

1. À chaque indice trouvé, une capture d'écran où l'on voit **la commande qui t'a débloqué et son résultat**.
   **Cinq captures au total.**

2. Interdit de spoiler les chemins, les mots de passe ou le code dans les salons. Le plaisir des autres en dépend.

3. Coincé plus de 30 minutes ? Poste dans `#sos-debug` ce que tu as tenté. Tu recevras une piste, jamais la réponse.

4. Le code du coffre ne va **que dans ton mail**.

---

# Étape 4 — Le compte rendu à envoyer

**Par mail à [meggieonthestack@gmail.com](mailto:meggieonthestack@gmail.com), avant mercredi 5 août à 15 h 00 GMT+2.**

En objet, écris :

> **Mission 2 — [ton pseudo Discord] — [TON VRAI NOM] — [ton pays]**

Cela permet de s'y retrouver avec les différences d'heures.

Le compte rendu est **écrit à la main, avec tes mots, sans IA**.

Court et honnête : **quinze lignes de texte suffisent**.

Il doit contenir six choses :

1. Tes réponses aux **4 questions de la théorie**, une phrase chacune.
2. Ton **screenshot de la mise en jambes**.
3. Tes **5 captures de la chasse**, une par indice.
4. Le **code trouvé dans le coffre**.
5. La **commande que tu as découverte pendant la chasse et qui t'a le plus servi**, avec une phrase sur ce qu'elle fait.
6. **Où tu as bloqué et comment tu t'en es sorti**, ainsi qu'une question que tu veux qu'on traite au lab, le soir même.

---

# Mercredi soir — Le lab

## La Mission 3 se fait en direct

**Mercredi 20 h 00 GMT+2**, dans le vocal **Coworking**.

Ce n'est pas un cours et ce n'est pas une réunion.

C'est la **Mission 3 du sprint**, sur les processus et `systemd`, et on la fait ensemble, en direct, chacun sur sa machine.

Et on ne va pas installer le programme de quelqu'un d'autre.

Tu vas **écrire ton propre service Linux**, de tes mains.

Un programme qui :

* surveille ta machine ;
* tourne en boucle sans jamais s'arrêter ;
* redémarre tout seul à chaque allumage.

Exactement ce qui tourne sur les vrais serveurs en production.

**Pendant 1 h 30, ensemble.**

### Au programme

1. On ouvre le capot de ta machine. Tu la regardes vivre en temps réel et tu tues ton premier processus de tes mains.

2. Tu écris ton service, ligne par ligne, et tu le mets en production avec les gestes d'un admin. Puis ta machine se met à te parler en direct dans son journal, à travers un programme que tu auras écrit deux minutes plus tôt.

3. Et je te préviens pour la suite. Après le direct, ta machine va tomber en panne. Trois pannes en même temps, provoquées par moi, comme une vraie nuit d'astreinte.

   Tu devras tout remettre debout, seul, avec les outils que tu viens d'apprendre.

   Un code t'attend au bout.

## Ce qu'il faut pour en profiter

Ta VM démarrée avant **20 h 00 GMT+2**, et tes questions des missions 1 et 2.

On les traite en direct.

Rien d'autre.

Pas besoin d'avoir tout réussi jusqu'ici, ceux qui ont bloqué se font justement rattraper là.

### Tu ne peux vraiment pas être là ?

Pas de panique.

La Mission 3 arrive aussi en doc complet et tu la feras à ton rythme, panne comprise.

Mais le direct, c'est là que la promo devient une équipe.

**Clique "Intéressé" ici pour recevoir la notification au démarrage :**

[Événement Discord — Mission 3](https://discord.com/events/1531360296869040360/1533752289247105034)

---

# Si tu bloques

Direction `#sos-debug` sur le serveur, à n'importe quelle heure.

Poste ton message d'erreur **en entier, copié-collé**, pas une description.

Pour la chasse, montre ce que tu as tenté : tu recevras une piste, pas la réponse.

On debug ensemble, c'est fait pour ça.

Tu n'as pas encore rendu la mission 1 ? Rien n'est perdu, personne ne court.

Envoie ce que tu as, même incomplet, et enchaîne sur celle-ci.
