# Proxmox - Neue Festplatten btrfs einbinden

## Einzelnes Laufwerk
1. Mit `fdisk -l` herausfinden, welchen Namen die neue Festplatte hat. Bsp. /dev/sda
2. Mit `mkfs.btrfs -fL %VolumenName% %Pfad%` also `mkfs.btrfs -fL Main /dev/sda` das btrfs Volume erstellen.
3. Anschließend wird eine UUID angezeigt, diese in der Zwischenablage abspeichern.
4. Einen beliebigen Mountpoint erstellen. Bsp. `/mnt/Main`
5. Folgenden Eintrag in der /etc/fstab hinzufügen 
```UUID=xxx /mnt/Main btrfs defaults 0 0``` 
6. Mit `mount -a` wird das Laufwerk eingebunden.

## RAID

1. Mit `fdisk -l` herausfinden, welche Festplatten kombiniert werden sollen. `/dev/sda /dev/sdb`
2. Mit `mkfs.btrfs -f -m raid0 /dev/sdd /dev/sde` das Raid erstellen.
3. Anschließend wird eine UUID angezeigt, diese in der Zwischenablage abspeichern.
4. Einen beliebigen Mountpoint erstellen. Bsp. `/mnt/Main`
5. Folgenden Eintrag in der /etc/fstab hinzufügen 
```UUID=xxx /mnt/Main btrfs defaults 0 0``` 
6. Mit `mount -a` wird das Laufwerk eingebunden.
7. Mit `df -h %Pfad%` kann die größe des RAIDs eingesehen werden

	![[Pasted image 20211103190155.png]]
