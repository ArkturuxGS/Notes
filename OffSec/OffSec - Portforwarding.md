# OffSec - Portforwarding

Sollte es einen Listener auf Loopback geben z.B. 127.0.0.1:8000 kann dieser via SSH Portforwarding auf den lokalen Rechner weitergeleitet werden.

Auf dem Pentest-Rechner die Datei id_rsa.pub öffnen und den Inhalt in die authorized_keys des Zieles eingeben.

Mit `ssh -L 8000:127.0.0.1:8000 user@ziel` die Verbindung aufrufen. 


