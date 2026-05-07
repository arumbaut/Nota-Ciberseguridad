-  apt install libpam-google-authenticator
- nano /etc/pam.d/sshd
```bash
###   Agregar 2FA
auth required pam_google_authenticator.so
```

- nano /etc/ssh/sshd_config
```bash
#### Cambiamos la sig linea a yes
KbdInteractiveAuthentication yes
```