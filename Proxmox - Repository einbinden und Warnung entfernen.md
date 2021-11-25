# Proxmox - Repository einbinden und Warnung entfernen

## Repo hinzufügen
1. /etc/apt/sources.list im beliebigen Editor öffnen
2. `deb http://download.proxmox.com/debian/pve bullseye pve-no-subscription` hinzufügen
3. In Proxmox WebUI unter "Updates" -> "Repositories" -> "Reload" klicken. Das neue Repository ist nun hinzugefügt.

## Login Warnung entfernen

### Easy Mode

Folgenden Befehl ausführen:
```
sed -i.backup -z "s/res === null || res === undefined || \!res || res\n\t\t\t.data.status.toLowerCase() \!== 'active'/false/g" /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js && systemctl restart pveproxy.service 
```
