# Nextcloud Installation

Die folgende Installation findet unter #Proxmox in einem #LXC Container statt. Es kann daher sein, dass die Installation an einigen Stellen abweicht.
Für die Installation von #Nextcloud ist es wichtig, einen Server mit mySQL und PHP-Unterstützung zur Verfügung steht.

1. Container mit Debian erstellen. Empfohlen sind mindestens 4GB RAM. Kerne sind vom System abhängig.
Für eine detaillierte Anleitung zur Installation von #LXC Containern unter Proxmox siehe:  [[Proxmox - Erstellung LXC Container]]

2.  Via SSH auf dem Container anmelden. Nutzerdaten hierfür sind "root" und das bei der Installation festgelegte Passwort
3.  `apt-get update && apt-get upgrade -y `
4. Wie oben erwähnt, wird für #Nextcloud eine mySQL und PHP Installation erfordert. Dies bietet LAMP-Server `apt install lamp-server`
5. Zusätzlich werden noch weitere PHP-Module für die #Nextcloud benötigt
`apt install php-zip php-dompdf php-xml php-mbstring php-gd php-curl php-imagick php-intl unzip`
6. Für eine performantere #Nextcloud weisen wir PHP mehr RAM zu:
`nano /etc/php/`