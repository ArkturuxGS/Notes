# Synology - Linux Share erstellen und Mouten

## Einrichtung in der Synology - NFS aktivieren

1. Im DSM einloggen
2. Systemsteuerung aufrufen
3. Die Option "Dateidienste" wählen
4. Den Reiter "NFS" auswählen
5. NFSv4.1 auswählen

![[Pasted image 20211027094620.png]]

## Einrichtung in der Synology - Ordner Freigabe

In meinem Fall ist es so, dass ich einen Transfer Ordner erstellen möchte, in dem ich zwischen meinen Linux Rechnern und meinen Windows-PCs Daten auf die Schnelle austauschen kann.
Hierzu habe ich unter "Freigegebener Ordner" einen Ordner mit dem Namen "Transfer" erstellt.

Um die NFS Berechtigungen zuerteilen, geht man wie folgt vor:

1. Ordner auswählen
2. "Bearbeiten" anklicken
3. In den Tab "NFS-Berechtigungen" wechseln
4. Auf "Erstellen" klicken

![[Pasted image 20211027095154.png]]

Hier nun lediglich die IP-Adresse des Hosts eingeben, welcher sich mit dem Share verbinden darf.

Speichern nicht vergessen!

## Linux - Share mounten

1. Mountpoint erstellen. Am besten unter /mnt/. In meinem Beispiel `mkdir /tmp/Transfer`
2. `sudo mount -t nfs [IP-Der-Synology]:/[Pfad-Zum-Ordner] [MountPoint]`

	Beispiel
	`sudo mount -t nfs 192.168.178.245:/volume1/Transfer /mnt/Transfer
