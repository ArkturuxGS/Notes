# Proxmox - Repository einbinden und Warnung entfernen

## Repo hinzufügen
1. /etc/apt/sources.list im beliebigen Editor öffnen
2. `deb http://download.proxmox.com/debian/pve bullseye pve-no-subscription` hinzufügen
3. In Proxmox WebUI unter "Updates" -> "Repositories" -> "Reload" klicken. Das neue Repository ist nun hinzugefügt.

## Login Warnung entfernen

### Easy Mode

Folgenden Befehl ausführen:
```
sed -Ezi.bak "s/(Ext.Msg.show\(\{\s+title: gettext\('No valid sub)/void\(\{ \/\/\1/g" /usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js && systemctl restart pveproxy.service 
```

### Manuell

1. `cd /usr/share/javascript/proxmox-widget-toolkit`
2. `cp proxmoxlib.js proxmoxlib.js.bak`
3. `nano proxmoxlib.js`
4. ```
Ext.Msg.show({
  title: gettext('No valid subscription'),
```