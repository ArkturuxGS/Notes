# OffSec - Intelligente Shell

Upgrade von einer "dummen" PHP-Reverseshell zu einer intelligenten Shell:

- python3 -c 'import pty;pty.spawn("/bin/bash")' 
- export TERM=xterm 
- Ctrl + Z 
- stty raw -echo; fg

