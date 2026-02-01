# ha-inet

## Description
Package ha-inet contenant le service ha-inet.
Ce service vérifie l'état d'une interface et passe un noeud Proxmox en mode maintenance si elle devient DOWN.
L'état UP de l'interface fait sortir le noeud du mode maintenance.
En cas de problème sur l'interface de plusieurs noeuds, seul le premier noeud passera en mode maintenance afin d'éviter un passage de tous les noeuds en maintenance en cas de blackout.

**Attention**, ce script est utilisé pour vérifier les réseaux acheminés aux VMs, il ne doit pas surveiller l'interface du réseau dédié au fonctionnement du cluster!

Dépend du package pve-ha-manager.


## Création du .deb
Réalisez un clone du dépôt :

`git clone https://github.com/SIOFulbert/ha-inet.git`

Renommez le dossier **ha-inet** en **ha-inet_1.1-1_all** et utilisez la commande dpkg-deb pour créer le .deb :

`dpkg-deb --build ha-inet_1.1-1_all`

## Installation
Installez le paquet normalement avec dpkg :

`dpkg -i ha-inet_1.1-1_all.deb`

Le package est généré dans le répertoire courant.

## Configuration
Configurez l'interface à surveiller dans le fichier /etc/default/ha-inet :

`IFACE=eth0`

## Utilisation

Il est possible de se passer du service et d'utiliser directement la commande pour lancer unevérification :

`ha-inet [interface]`

Si aucun paramètre n'est passé, c'est l'interface renseignée dans le fichier /etc/default qui sera prise en compte.
