# Compte Rendu

## Istallation

- J'ai utilisé la vbox préinstallé 'licenceProPreInstalled-2024'

## Post-Installation

>1.Configuration SSH sur la machine Virtuelle

**apt search ssh** puis **apt install ssh**  

- Les paquets SSH ont bien été installé.

**sudo systemctl start ssh**

- Demarre le service SSH

**nano /etc/ssh/sshd_config**

- Modification du fishier sshd_config  

- Changement de PasswordAuthentification 

**systemctl restart ssh**

- Redemarre le serveur SSH

>2.Connection

**ssh root@10.20.0.136**

- Connecte le hote au serveur ssh 

>3.Nombre de paquets

**dpkg -l | wc -l**

### Résultat : 

- 326 paquets installé 

>4.Space Usag

**df -h**

### Résultat :

<pre>
Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
udev               4,9G       0  4,9G   0% /dev
tmpfs              995M    564K  994M   1% /run
/dev/sda1          9,1G    1,6G  7,0G  19% /
tmpfs              4,9G       0  4,9G   0% /dev/shm
tmpfs              5,0M       0  5,0M   0% /run/lock
/dev/sda2          3,6G     40K  3,4G   1% /tmp
/dev/sda3          921M     31M  827M   4% /var/log
tmpfs              995M       0  995M   0% /run/user/0
</pre>

>5.Expliquer les commandes et le resultat obtenu

**echo $LANG**

### Résultat :

- La commande affiche la langue et les paramètres régionaux utilisés par le système 

<pre>
      fr_FR.UTF-8
</pre>

**hostname**

### Résultat :

- Affiche le nom d'hôte de la machine

<pre>
      serveur-correction
</pre>


**hostname -d**

### Résultat :

- Affiche le domaine d'un système

**cat /etc/apt/sources.list | grep -v -E ’^#|^$’**

### Résultat :

- Affiche les dépôts de paquets actifs configurés sur le système

<pre>
      deb http://deb.debian.org/debian/ bookworm main contrib non-free non-free-firmware
      deb http://security.debian.org/debian-security bookworm-security main contrib non-free non-free-firmware
      deb http://deb.debian.org/debian/ bookworm-updates main contrib non-free non-free-firmware
</pre>
  
**cat /etc/shadow | grep -vE ’:\*:|:!\*:’**

### Résultat :

- Affiche les compte ayant un mot de passe
  
<pre>
      root:$y$j9T$cGKpM0Fh8WZYM4MlsbdWz0$hO26Ub/deBLYO3CleXEevZ8v/V.ItKMLsZ274x5BMtA:19635:0:99999:7:::
      messagebus:!:19635::::::
      sshd:!:19998::::::
</pre>

**cat /etc/passwd | grep -vE 'nologin|sync'**

### Résultat :

- Affiche les compte utilisateur

<pre>
      root:x:0:0:root:/root:/bin/bash
</pre>

**fdisk -l**

### Résultat :

- Affiche la liste des partitions du disque 

<pre>
<b>Disque /dev/sda : 20 GiB, 21474836480 octets, 41943040 secteurs</b>
Modèle de disque : HARDDISK        
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d&apos;E/S (minimale / optimale) : 512 octets / 512 octets
Type d&apos;étiquette de disque : gpt
Identifiant de disque : 3ED2EBFD-8995-4690-8EEF-8C65108F2339

<b>Périphérique</b> <b>   Début</b> <b>     Fin</b> <b>Secteurs</b> <b>Taille</b> <b>Type</b>
/dev/sda1        2048 19531775 19529728   9,3G Système de fichiers Linux
/dev/sda2    19531776 27344895  7813120   3,7G Système de fichiers Linux
/dev/sda3    27344896 29298687  1953792   954M Système de fichiers Linux
/dev/sda4    29298688 41940991 12642304     6G Partition d&apos;échange Linux
</pre>

**fdisk -x**

### Résultat :

- Fournit des information avancées sur la disposition physique des disques

<pre>
<b>Disque /dev/sda : 20 GiB, 21474836480 octets, 41943040 secteurs</b>
Modèle de disque : HARDDISK        
Unités : secteur de 1 × 512 = 512 octets
Taille de secteur (logique / physique) : 512 octets / 512 octets
taille d&apos;E/S (minimale / optimale) : 512 octets / 512 octets
Type d&apos;étiquette de disque : gpt
Identifiant de disque: 3ED2EBFD-8995-4690-8EEF-8C65108F2339
Premier LBA utilisable: 34
Dernier LBA utilisable: 41943006
LBA alternatif: 41943039
LBA de départ des entrées de partition: 2
Entrées de partitions allouées: 128
LBA de fin des entrées de partition: 33

<b>Périphérique</b> <b>   Début</b> <b>     Fin</b> <b>Secteurs</b> <b>Type-UUID                           </b> <b>UUID                                </b> <b>Nom       </b> <b>Attr.</b>
/dev/sda1        2048 19531775 19529728 0FC63DAF-8483-4772-8E79-3D69D8477DE4 7202EEDF-B999-47CC-BE80-70C80C2C83B0 la racine  
/dev/sda2    19531776 27344895  7813120 0FC63DAF-8483-4772-8E79-3D69D8477DE4 346085A8-A5AE-48BA-B6B7-BDA598DD7465 espace tempo
                                                                                                                             
/dev/sda3    27344896 29298687  1953792 0FC63DAF-8483-4772-8E79-3D69D8477DE4 8F880167-DE17-4896-BB95-EE5AAC9E2E9A les logs   
/dev/sda4    29298688 41940991 12642304 0657FD6D-A4AB-43C4-84E5-0933C84B4F4F 68C18C76-59A6-45DF-A745-F87FD1D412DA ma swap</pre>

>6.Installation automatique

**preseed**

- C'est une methode permettant d'automatiser l'installation du système d'exploitation Debian et de ses dérivés

>7.Rescue mode

- Dans le mode de recupération, on selectionne 'root'
- Sur le message il faut appuyer sur la touche entrée
- Ensuite pour réinitialiser le mot de passe de l’utilisateur 'root', on utilise la commande passwd de cette manière :
  
<pre>
      passwd root 
</pre>

- On saisie le mot de passe 
- Enfin 'exit' pour revenir au menu de récupération

>Redimentionnement partition

- On peut redimensionner une partition avec l'outil **GParted**

#### Étapes :
**Installation de GParted**
   - on l'installe via la commande suivante :
     <pre>
     sudo apt install gparted
     </pre>

**Lancement de GParted**
   - lancement du GParted :
     <pre>
     sudo gparted
     </pre>

**Sélection du disque**
   - il faut sélectionner le disque contenant la partition à redimensionner.

**Redimensionner la partition**
   - clic droit sur la partition qu'on veux redimensionner, puis sur **Redimensionner/Déplacer**.

**Appliquer les modifications**
   - Appliquer les modifications.
