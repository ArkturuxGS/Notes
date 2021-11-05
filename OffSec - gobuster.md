# gobuster
Autor: Fabian Zertani

## Beschreibung
gobuster ist ein #Commandlinetool zum bruteforcen  von URLs und gehört zu den #Enumerationtools.
Da gobuster mit #Dictionaries arbeitet, benötigt das Tool #Wordlisten

### Wordlist
gobuster Wordlists:
- [common.txt](https://github.com/digination/dirbuster-ng/blob/master/wordlists/common.txt)
- [small.txt](https://github.com/daviddias/node-dirbuster/blob/master/lists/directory-list-2.3-small.txt)
- [medium.txt](https://github.com/daviddias/node-dirbuster/blob/master/lists/directory-list-2.3-medium.txt)
- [big.txt](https://github.com/daviddias/node-dirbuster/blob/master/lists/directory-list-2.3-big.txt)
- [CMS-Wordlists](https://github.com/JavierOlmedo/UltimateCMSWordlists)

Ist die Art des HTTP Server hinter der Webseite bekannt, macht es Sinn mit einer Wordlist, die spezifisch für die Art von Server ausgelegt ist, fortzufahren.
An dieser Stelle lohnt es sich einen Blick in die Wordlistsammlung von Daniel Miessler zu werfen:

[Web-Content-Wordlist](https://github.com/danielmiessler/SecLists/tree/master/Discovery/Web-Content)

### Anwendungsbeispiel

`gobuster dir -u https://operational-services.de -w %PfadWordList% -x php,txt,html -o output.txt` 

Im Beispiel ruft gobuster mit der Flag `dir -u` die Webseite der OS auf und hängt durch den Zusatz `-x`am Ende des Strings jeweils ein Wort aus der Wordlist mit jeweils den Dateiendungen "php" "txt" "html".

Beispiel: https://operational-services.de/admin.html

Durch die Option `-o` werden die Ergebnisse in der angegebenen Datei abgespeichert.

Weitere gobuster Befehle sind unter [[gobuster Cheatsheet]] zu finden.