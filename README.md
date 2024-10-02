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

<pre>Sys. de fichiers Taille Utilisé Dispo Uti% Monté sur
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

- Affiche le nom d'hôte de la machine

- 'serveur-correction'

**hostname -d**

- Affiche le domaine d'un système

**cat /etc/apt/sources.list | grep -v -E ’^#|^$’**

- Affiche les dépôts de paquets actifs configurés sur le système 

**cat /etc/shadow | grep -vE ’:\*:|:!\*:’**

