- Tags : #apache #securizar #configurar #proteger #limitar_acceso

```bash
#Aqui se encuentra la configuracion del servidor web tanto http como https
❯ cd /etc/apache2/sites-available
❯ ls
000-default.conf default-ssl.conf
❯ sudo nano 000-default.conf

<Files "secret.txt">
	Required all denied
</Files>

❯ sudo systemctl restart apache2
❯ sudo a2sensite 000-default.conf  #Activa la configuracion 
```