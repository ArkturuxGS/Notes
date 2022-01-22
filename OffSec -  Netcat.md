# OffSec -  Netcat

## Datenübertragung
Mit #Netcat kann man auch Daten #übertragen. 
Hierzu ist wie folgt vorzugehen.

Auf dem Client wird eim TCP-Listening Port geöffnet und der Output in eine "incoming.exe" geschrieben

`nc -nlvp 4444 > incoming.exe`

Auf dem Host wird nun der folgende Befehl eingesetzt:

`nc -nv 10.11.0.22 4444 < /usr/share/windows-resources/binaries/wget.exe`

## Netcat Bind Shell

