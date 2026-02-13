	- Tags: #nuclei #recursos #recursos_github 

```bash
nuclei -u http://ip:port

nuclei -update-templates  #actualizar las plantillas de nuclei
```

**Recursos**: Plantillas de nuclei [https://github.com/coffinxp/nuclei-templates](https://github.com/coffinxp/nuclei-templates)

```bash
#Utilizar plantilla especifica
nuclei -u http://ip:port -t dir-nuclei-template/nombre-plantilla.yml  

#Utilizar todas las plantillas de la folder indicada
nuclei -u http://ip:port -t dir-nuclei-template/.  

```