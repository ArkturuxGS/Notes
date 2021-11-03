# Proxmox - Neue Festplatten btrfs einbinden

1. Mit `fdisk -l` herausfinden, welchen Namen die neue Festplatte hat. Bsp. /dev/sda
2. Mit `mkfs.btrfs -fL %VolumenName% %Pfad%` also `mkfs.btrfs -fL Main /dev/sda` das btrfs Volume erstellen.
3. Anschließend wird

