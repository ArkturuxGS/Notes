# OffSec - Powershell und Powercat

## Execution Policy

Um #Powershell effektiv in einem #Penetrationtest verwenden zu können, muss die #Execution-Policy auf "Unrestricted" gesetzt werden.

`Set-ExecutionPolicy Unrestricted`

Mit folgendem Befehl kann überprüft werden, wie die Execution-Policy gesetzt ist:

`Get-ExecutionPolicy`

## File Transfers

Mit #Powershell können auch #FileTransfers durchgeführt werden.
Wie folgt wird ein #Download vorgenommen - Vorausetzung ist, dass auf dem Host ein HTTP-Server eröffnet wurde:




