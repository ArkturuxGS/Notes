# OffSec - Socat 

## File Transfer

Listener mit Socat auf dem Host öffnen, um Daten zu empfangen und in eine Datei zu schreiben 

````
socat TCP4-LISTEN:443,fork file:secret_passwords.txt
````