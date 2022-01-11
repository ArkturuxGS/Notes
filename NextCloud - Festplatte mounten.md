# Proxmox -  NextCloud - Festplatte mounten
Um Daten außerhalb des Containers zu speichern, sind folgende Schritte nötig:

1. An den Container via SSH anmelden
2. Unter /mnt/ einen Ordner erstellen. Zum Beispiel `mkdir /mnt/storage`
3. Container herunterfahren
4. Container auswählen -> unter Ressourcen -> Hinzufügen "Mount Point" auswählen

![[Pasted image 20220111151221.png]]