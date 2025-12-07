# ha-inet

## Description
Service ha-inet qui vérifie l'état d'une interface et passe le noeud en mode maintenance si elle passe en mode DOWN.
En cas de problème sur plusieurs noeuds, seul le premier noeud passera en mode maintenance afin d'éviter un passage global en maintenance en cas de blackout.

Attention, ce script ne doit pas surveiller le réseau dédié au fonctionnement du cluster et ce dernier doit être physiquement isolé!

Dépend du package pve-ha-manager doit être installé.

## Configuration
Configurez l'interface à surveiller dans le fichier /etc/default/ha-inet :
`IFACE=eth0`

## Utilisation

Il est possible de se passer du service et d'utilsier manuellement la vérification :
`ha-inet [interface]`

Si aucun paramètre n'est passé, c'est l'interface renseignée dans le fichier /etc/default qui sera prise en compte.