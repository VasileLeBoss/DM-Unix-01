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

**ssh serveur-correction@127.0.0.136**

### Résultat : 



>3.Nombre de paquets

**dpkg -l | wc -l**

### Résultat : 

- 326 paquets installé 

>4.Space Usag

**df -h**

### Résultat :

- Dans le terminal on obtien l'espace disque utilisé et disponible sur le système

- Format : Sys.de fichiers / Taille / Utilisé / Dispo / Uti% / Monté sur /

>5.Expliquer les commandes et le resultat obtenu

**echo $LANG**

### Résultat :

- La commande affiche la langue et les paramètres régionaux utilisés par le système 

- 'fr_FR.UTF-8'

**hostname**

- Affiche le nom d'hôte de la machine

- 'serveur-correction'

**hostname -d**

- Affiche le domaine d'un système

**cat /etc/apt/sources.list | grep -v -E ’^#|^$’**

- Affiche les dépôts de paquets actifs configurés sur le système 

**cat /etc/shadow | grep -vE ’:\*:|:!\*:’**

