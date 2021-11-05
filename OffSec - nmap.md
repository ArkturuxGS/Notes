# nmap
## Beschreibung

Mit Nmap (Network Mapper) können offene Ports an jedem Host gescannt werden. Nmap gehört zu den #Enumerationtools. 

### Beispiel:
`sudo nmap -A -T4 -p- %TargetIP% -oN %PFAD%/scan`

Im oben genannten Beispiel muss Nmap als Root ausgeführt werden, da für den Parameter `-A` (Aggressiv Scan) erweiterte Rechte benötigt werden. Durch den Parameter `-A` führt Nmap automatisch eine OS-Detection, Version-Detection, Script-Scanning und Trace Routing durch .

`-T4` steht für das Timing. Es kann eine Zahl zwischen 0 und 5 festgelegt werden. Je höher die Zahl, desto schneller der Scan, aber auch das Risiko von einem IDS abgefangen zu werden.

`-p-` Steht für die Portrange, die beim Scan abgegriffen wird. `-p-` beschreibt alle 65535 Ports. Es können aber auch einzelne Ports gescannt werden. Beispiel: Für die Ports 439 und 445 kann man -p 439,445 angeben. Für alle Ports zwischen 439 und 445 -p 439-445

Mit dem Zusatz `-oN` und der Angabe eines Pfades, kann man den Scan parallel in einer Textdatei abspeichern.

Für weitere Befehle siehe [[nmap Cheatsheet]]