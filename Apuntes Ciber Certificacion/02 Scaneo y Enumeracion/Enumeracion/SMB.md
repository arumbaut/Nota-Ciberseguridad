### Windows Discaovered

```ps1
#Conectar
net use z:\\10.10.4.133\c$ user_pass /user:admin

#Descaonectar
net use *  /delete 
```


### NMAP
```bash
#SMB Nmap Scripts

nmap -p 445 --script smb-protocols ip

nmap -p 445 --script smb-security-mode ip

nmap -p 445 --script smb-enum-sessions --script-args smbusername=user,smbpassword=pass ip

nmap -p 445 --script smb-enum-shares --script-args smbusername=user,smbpassword=pass ip

nmap -p 445 --script smb-enum-users --script-args smbusername=user,smbpassword=pass ip

nmap -p 445 --script smb-server-stats --script-args smbusername=user,smbpassword=pass ip

nmap -p 445 --script smb-enum-domains --script-args smbusername=user,smbpassword=pass ip

nmap -p 445 --script smb-enum-groups --script-args smbusername=user,smbpassword=pass ip

nmap -p 445 --script smb-enum-services --script-args smbusername=user,smbpassword=pass ip

nmap -p 445 --script smb-enum-shares,smb-ls --script-args smbusername=user,smbpassword=pass ip
```