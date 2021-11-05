# Offsec - Linux Priviledge Escalation

## User Enumeration

- `whoami`
- `id`
- `sudo -l`
- `cat /etc/passwd`
- `ls -la /etc/shadow`

## OS Enumeration

- `cat /etc/issue`
- `cat /etc/*-release*`
- `cat /proc/version`
- `uname -a`
- `arch`
- `ldd -version`

## Crontabs

- `ls -lah /etc/cron*`
- `cat /etc/crontab`
- `ls -la /var/log/cron*`
- `find / -name cronlog 2>/dev/null`

## Ports checken
- `lsof -Pni`
- `Netstat -antp`

## SUID Bit suchen
- ``find / -type f \( -perm -4000 -o -perm -2000 \) -exec ls -l {} \;``