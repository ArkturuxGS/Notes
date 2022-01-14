# OffSec - Portforwarding

Sollte es einen Listener auf Loopback geben z.B. 127.0.0.1:8000 kann dieser via SSH Portforwarding auf den lokalen Rechner weitergeleitet werden.

1. `ssh-keygen`
2. `cat id_rsa.pub`
3. Den erzeugten Schlüssel nun in eine authori