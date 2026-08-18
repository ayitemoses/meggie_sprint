#:

Pour savoir quel Shell j’utilise :

```bash
echo $SHELL
````

On obtient souvent :

```text
/bin/bash
```

---

## 2. Il y a quoi dans `/home`, dans `/etc`, dans `/var` ?

### `/home`

C’est le répertoire des données personnelles des utilisateurs.

Par exemple, si ton nom utilisateur est `moses`, alors ton répertoire personnel est :

```text
/home/moses
```

### `/etc`

Contient principalement les fichiers de configuration du système Linux et des services.

### `/var`

Contient les données variables et les **logs** qui changent fréquemment ou qui sont modifiés régulièrement par le système et les applications.

---

## 3. Chemin absolu, chemin relatif, quelle différence ?

### Chemin absolu

Un chemin absolu commence par `/`.

Exemple :

```bash
cat /home/moses/Documents/fichier.txt
```

### Chemin relatif

Un chemin relatif ne commence pas par `/`.

Exemple :

Supposons que je suis ici :

```text
/home/moses
```

Et que je veux accéder au fichier précédent :

```bash
cat Documents/fichier.txt
```

### Différence

Le **chemin absolu** part toujours de `/`, alors que le **chemin relatif** part de mon emplacement actuel et ne commence pas par `/`.

---

## 4. Le symbole `|` fait quoi ?

`|` est appelé **pipe**.

Il permet d’envoyer la sortie d’une commande **A** vers l’entrée d’une commande **B**.

Exemple :

```bash
ls | grep Documents
```

Dans cet exemple :

* `ls` affiche les fichiers et dossiers ;
* `|` envoie le résultat de `ls` vers `grep` ;
* `grep Documents` filtre les résultats qui contiennent `Documents`.

On peut retenir :

> `|` = « prends le résultat de gauche et donne-le à droite ».

---

### Le symbole `~`

`~` représente le répertoire personnel de l’utilisateur.

Pour l’utilisateur `moses` :

```text
~ = /home/moses
```

Exemple :

```bash
cd ~
```

équivaut à :

```bash
cd /home/moses
```

Autre exemple :

```bash
cd ~/Downloads
```

équivaut à :

```bash
cd /home/moses/Downloads
```

---

### Le symbole `@`

`@` est notamment utilisé pour les utilisateurs et SSH.

Format :

```text
utilisateur@machine
```

Exemple :

```bash
ssh moses@192.168.1.10
```

Ici :

* `moses` = utilisateur ;
* `192.168.1.10` = machine.

---

### Le symbole `#`

`#` peut représenter :

* **root** dans le prompt du terminal ;
* un **commentaire** dans un script Shell.

Exemple de commentaire :

```bash
# Ceci est un commentaire
```

Exemple de prompt root :

```text
root@machine:~#
```

---

### Le symbole `$`

`$` peut représenter :

* une variable ;
* le prompt d’un utilisateur normal.

Exemple avec une variable :

```bash
echo $SHELL
```

Exemple de prompt utilisateur normal :

```text
moses@machine:~$
```

---

## Autres symboles essentiels

| Symbole | Signification                       | Symbole     | Signification                                                   |
| ------- | ----------------------------------- | ----------- | --------------------------------------------------------------- |
| `/`     | Racine ou séparateur de chemins     | `&`         | Lancer en arrière-plan                                          |
| `.`     | Répertoire actuel                   | `&&` (ET)   | Exécuter la deuxième commande si la première réussit            |
| `..`    | Répertoire parent                   | `;`         | Séparer plusieurs commandes                                     |
| `~`     | Home de l’utilisateur `/home/moses` | `$`         | Variable / prompt utilisateur                                   |
| `` ` `` | Substitution de commande            | `#`         | Commentaire / prompt root                                       |
| `>`     | Rediriger la sortie vers un fichier | `*`         | Joker (plusieurs fichiers)                                      |
| `>>`    | Ajouter à la fin d’un fichier       | `\|`        | Pipe : envoyer la sortie de la commande A vers l’entrée de la B |
| `<`     | Prendre l’entrée depuis un fichier  | `\|\|` (OU) | Exécuter la deuxième commande si la première échoue             |


## 5. Resumé des commandes de OverTheWire Level 0 to Level 6

find . -type f -name '-*'

cat -- ./-filename

cat .hidden

cat ./-

cat ./-filename

cat -- "--filename"

ssh bandit0@bandit.labs.overthewire.org -p 2220

bandit5@bandit:~$ find inhere/ -type f -size 1033c ! -executable

pXa26xhMWaC2SvDotA4r9EgZkulOeSBW

