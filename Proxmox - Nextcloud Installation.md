# Nextcloud Installation

Die folgende Installation findet unter #Proxmox in einem #LXC Container statt. Es kann daher sein, dass die Installation an einigen Stellen abweicht.
Für die Installation von #Nextcloud ist es wichtig, einen Server mit mySQL und PHP-Unterstützung zur Verfügung steht.

1. Container mit Debian erstellen. Empfohlen sind mindestens 4GB RAM. Kerne sind vom System abhängig.
Für eine detaillierte Anleitung zur Installation von #LXC Containern unter Proxmox siehe:  [[Proxmox - Erstellung LXC Container]]

2.  Via SSH auf dem Container anmelden. Nutzerdaten hierfür sind "root" und das bei der Installation festgelegte Passwort

3.  `apt-get update && apt-get upgrade -y `

4. Wie oben erwähnt, wird für #Nextcloud eine mySQL und PHP Installation erfordert. Dies bietet LAMP-Server `apt install lamp-server`

5. Zum Download der Nextcloud Software empfiehlt es sich direkt den neusten Release zu nehmen.
`cd /tmp && wget https://download.nextcloud.com/server/releases/latest.zip `

In das Verzeichnis des Nextcloud-Downloads wechseln.
Mit `unzip latest.zip` das Archiv entpacken.

Die Daten mit:
`mv nextcloud /var/www`
In das Hostverzeichnis verschieben.

## Konfiguration PHP
Zusätzlich werden noch weitere PHP-Module für die #Nextcloud benötigt
`apt install php-zip php-dompdf php-xml php-mbstring php-gd php-curl php-imagick php-intl unzip`

Für eine performantere #Nextcloud weisen wir PHP mehr RAM zu:
`nano /etc/php/7.2/apache2/php.ini` (Die PHP-Version kann hier abweichen)
Mit CTRL+W nach dem eintrag "memory_limit" suchen.
Der Standartwert beträgt hier 128M
Das Limit sollte hier zwischen 1024M und 2048M liegen.

Damit größere Dateien als 2MB auf die Nextcloud hochgeladen werden können, muss auch dieses Limit angehoben werden. Dies geschieht in Zeile "upload_max_filesize" und "post_max_size" (Angaben können hier mit M oder G erfolgen. Um das Limit aufzuheben, kann hier eine 0 eingetragen werden)

Zum Schluss nur noch die Zeitzone anpassen. Dies geht unter der Zeile "date.timezone"
Hier einfach die Zeitzone hinterlegen z.B. "Europe/Berlin"

## Konfiguration mySQL

Mit dem Befehl `mysql_secure_installation` die Installation von mySQL starten.
Validate Password Login mit "N" ablehnen und im nächsten Schritt ein neues root Kennwort für die Datenbank festlegen.

Im nächsten Schritt auf jeden Fall den Anonymen Nutzer mit Y entfernen!
Bei der nächsten Abfrage wird angeboten, den root-login nur via Localhost zu erlauben. Dies ist mit Y zu bestätigen. Das Entfernen der Testdatenbank, sowie das neuladen der Priviledgetable sind mit Y zu bestätigen.

Mit mySQL nun die Kommandozeile der mySQL-Datenbank aufrufen.
Nun wird die Datenbank für die Nextcloud erstellt. Hierfür sind folgende Befehle nötig:

`CREATE DATABASE nextcloud;`
Nun wurde eine neue Datenbank mit dem Namen "Nextcloud" erstellt.

`CREATE USER 'nextclouduser'@'localhost' IDENTIFIED BY 'PASSWORD';`

An dieser Stelle sollte ein anderer Nutzername als "nextclouduser" und ein sicheres Passwort gewählt werden.

Nun erhält der Nutzer Zugriff auf die Datenbank
`GRANT ALL ON nextcloud.* TO 'nextclouduser'@'localhost' IDENTIFIED BY 'PASSWORD' WITH GRANT OPTION;`

Zum Schluss die Rechte mit `FLUSH PRIVILEDGES` aktualisieren.

## Konfiguration Apache

Als erstes wird eine Konfiguartionsdatei für die Nextcloud erstellt:

`nano /etc/apache2/sites-available/nextcloud.conf`

```
<VirtualHost *:80>
     ServerAdmin master@domain.com
     DocumentRoot /var/www/nextcloud/
     ServerName demo.domain.com
     ServerAlias www.demo.domain.com
  
     Alias /nextcloud "/var/www/nextcloud/"

     <Directory /var/www/nextcloud/>
        Options +FollowSymlinks
        AllowOverride All
        Require all granted
          <IfModule mod_dav.c>
            Dav off
          </IfModule>
        SetEnv HOME /var/www/nextcloud
        SetEnv HTTP_HOME /var/www/nextcloud
     </Directory>

     ErrorLog ${APACHE_LOG_DIR}/error.log
     CustomLog ${APACHE_LOG_DIR}/access.log combined

</VirtualHost>
```


