# Nextcloud Installation

Die folgende Installation findet unter #Proxmox in einem LXC Container statt. Es kann daher sein, dass die Installation an einigen Stellen abweicht.

1. Container mit Debian 10 erstellen. Empfohlen sind mindestens 4GB RAM. Kerne sind vom System abhängig.
Für eine detaillierte Anleitung zur Installation von LXC Containern unter Proxmox siehe:  [[Proxmox - Erstellung LXC Container]]

2.  Via SSH auf dem Container anmelden. Nutzerdaten hierfür sind "root" und das bei der Installation festgelegte Passwort
3.  `apt`