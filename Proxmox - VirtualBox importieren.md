# Virtualbox Image in Proxmox importieren

## Speicher Ort der virtuellen Festplatte herausfinden

1. VirtualBox GUI öffnen
2. Auf die Migrierende VM klicken und "Ändern" auswählen
3. Auf "Massenspeicher" klicke und die Festplatte auswählen
4. Rechts am Rand befindet sich unter dem Punkt "Abgespeichert wo" der Pfad zur Festplatte
5. 
![[Pasted image 20211027074518.png]]

## vdi zu img konvertieren

1. Mit der Powershell in den Installationsordner von VirtualBox wechseln
2. Folgenden Befehl ausführen `VBoxManage clonehd --format RAW [virtual_harddisk].vdi [virtual_harddisk].img`
3.  Die Konvertierung kann etwas dauern

## Neue Proxmox VM erstellen

Speicher muss bei der VM mindestens genauso groß sein, wie der Speicher der exportierten Festplatte von VirtualBox.

Merken, auf welcher Festplatte die VM erstellt wurde und welche ID die Maschine hat.

## 