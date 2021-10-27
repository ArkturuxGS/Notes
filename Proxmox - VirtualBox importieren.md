# Virtualbox Image in Proxmox importieren

## Speicherort der virtuellen Festplatte herausfinden

1. VirtualBox GUI öffnen
2. Auf die Migrierende VM klicken und "Ändern" auswählen
3. Auf "Massenspeicher" klicke und die Festplatte auswählen
4. Rechts am Rand befindet sich unter dem Punkt "Abgespeichert wo" der Pfad zur Festplatte

![[Pasted image 20211027074518.png]]

## vdi zu img konvertieren

1. Mit der Powershell in den Installationsordner von VirtualBox wechseln
2. Folgenden Befehl ausführen `VBoxManage clonehd --format RAW [virtual_harddisk].vdi [virtual_harddisk].img`
3.  Die Konvertierung kann etwas dauern

## Neue Proxmox VM erstellen

Speicher muss bei der VM mindestens genauso groß sein, wie der Speicher der exportierten Festplatte von VirtualBox.

Merken, auf welcher Festplatte die VM erstellt wurde und welche ID die Maschine hat.

## Das neuerstellte img hochladen

Das Img in einem Netzlaufwerk bereitstellen und auf den Proxmox-Server unterfolgendem Pfad herunterladen:
`[PfadStorage]/images/[VMID]/[vmid]-disk0`

Beispiel:
`/mnt/SanDiskSSD/images/101/vm-101-disk-0`

Wenn die Übertragung über das Netzwerk stattfindet, bietet sich auf Grund der Größe, der Befehl `rsync -Pah` an

## Einbinden der neuen Festplatte

Im Pfad `[PfadStorage]/images/[VMID]/[vmid]-disk0` die alte Festplatte mit der Endung ".raw" löschen, oder in ".old" umbennen. 
Die neu importierte img in "disk.raw" umbennenen.

Der Import ist nun abgeschlossen und die Maschine kann gestartet werden


