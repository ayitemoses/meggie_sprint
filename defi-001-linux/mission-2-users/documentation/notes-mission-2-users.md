# Notes Mission 2 — Les users et les permissions

## 1. Root et un utilisateur normal, quelle différence

**Root** est l'utilisateur administrateur qui a tous les droits sur le système, alors qu'un utilisateur normal a seulement les permissions qui lui sont accordées.

## 2. Ce que fait vraiment sudo quand tu le tapes

**`sudo`** permet à un utilisateur autorisé d'exécuter une commande avec les droits d'un autre utilisateur, généralement `root`, sans se connecter directement en root.
sudo signifie **“superuser do”**

## 3. La ligne rwx d'un ls -l, comment on la lit. Propriétaire, groupe, autres

Dans `ls -l`, les permissions `rwx` se lisent en trois groupes : les droits du propriétaire, ceux du groupe et ceux des autres utilisateurs ; `r` signifie lecture(read), `w` écriture(write) et `x` exécution(execute).

**Les permissions rwx peuvent aussi être représentées par des chiffres : r=4, w=2, x=1; par exemple 777 donne tous les droits au propriétaire, au groupe et aux autres.**

### chmod 754 fichier donne donc : rwxr-xr-- avec cette repartition:

- 7 → rwx → propriétaire : lecture + écriture + exécution
- 5 → r-x → groupe : lecture + exécution
- 4 → r-- → autres : lecture seulement


## 4. Le principe du moindre privilège, c'est quoi et pourquoi ça te protège 

Le principe du moindre privilège consiste à donner à chaque utilisateur seulement les droits dont il a besoin, ce qui limite les dégâts en cas d'erreur ou de problème de sécurité. Ex: **RBAC** = Role-Based Access Control - contrôle d'accès basé sur les rôles.

## Résumé de commandes 

  117  whoami 
  118  id
  119  cat /etc/shadow
  120  sudo cat /etc/shadow | head -3
  121  ls -l ~/sprint/semaine-1/notes/jour-1.txt 
  122  chmod 600 ~/sprint/semaine-1/notes/jour-1.txt 
  123  ls -l ~/sprint/semaine-1/notes/jour-1.txt 
  124  chmod 644 ~/sprint/semaine-1/notes/jour-1.txt 
  125  ls -l ~/sprint/semaine-1/notes/jour-1.txt 
  126  chmod 664 ~/sprint/semaine-1/notes/jour-1.txt 
  127  ls -l ~/sprint/semaine-1/notes/jour-1.txt 
  128  history > myHistory.txt
  129  pwd
  130  ls
  131  tail myHistory.txt 
  132  cleqr
  133  clear
  134  ls
  135  cleqr
  136  clear
  137  cat chasse-002.sh 
  138  sudo bash chasse-002.sh 
  139  cd /opt/chasse/
  140  cat BIENVENUE.txt 
  141  ls -la
  142  cat ./.indice-1 
  143  cat ./.indice-2
  144  cat indice-2
  145  chmod 644 indice-2
  146  cat indice-2
  147  su -gardien
  148  su gardien
  149  cat indice-4
  150  sudo  cat indice-4
  151  find / -type f -name 'indice-5' 2>/dev/null
  152  find / -user gardien -type f -name 'indice-5' 2>/dev/null
  153  find / -user gardien -type f -name 'coffre*' 2>/dev/null
  154  cat /var/lib/.recoin/coffre-promo001 
  155  history > coffre.txt
  156  history > /home/moses/coffre.txt

  sudo usermod -aG promo001 moses # ajout d'un utilisateur a un groupe