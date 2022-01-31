# OffSec - Simple HTTP-Server

Um auf die Schnelle Daten einem anderen Client zur Verfügung zu stellen, kann man einen HTTP-Server mit Python erstellen.

Hierzu gibt es verschiedene Möglichkeiten. Die einfachste ist es, in den Ordner zu wechseln, der gehostet werden soll und dort den Server mit folgendem Befehl zu öffnen:

`python -m SimpleHTTPServer`

oder in Python3

`python3 -m http.server`

Dies wird den Server auf dem Port 8080 öffnen.

Andernfalls kann man mit dem Befehl

`python -m SimpleHTTPServer <port>` 

einen beliebigen Port angeben.

