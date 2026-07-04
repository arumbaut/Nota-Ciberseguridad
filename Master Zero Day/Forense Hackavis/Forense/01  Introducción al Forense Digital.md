- Tags: #forense #ftk_imager

### Herramientas : FTK Imager , Autopsy

Autopsy pasa scripts automatizados para detectar anomalías.
Recomendacion FTK para hacer Adquisiciones y Autopsy para Analizar

## SANS Digital Forensics and Incident Response Training  Free Resources
https://www.sans.org/cybersecurity-focus-areas/digital-forensics-incident-response

![[Pasted image 20260601162831.png]]

Cuando ocurre un Incidente de seguridad en una empresa lo primero que se debe hacer es hacer una adquisición de disco y de memoria RAM.

El orden de Adquisición se realiza por Volatilidad 
0 - Cache (Muy poco probable de obener info de esta )
1 - La RAM   (Si se ha apagado el ordenador pues es mas complicado hacer una adquisicion de esta pero es casi nulo si han pasado varias horas)
2 - Los discos duros
3 - Dispositivos  Conectados (USB, DD Externos)

### CyberDefenders , Plataforma para practicas Forense

FTK-Imager :para hacer adquisiciones y análisis manual es buena pero herramientas de pagos nos brindan mas Información .

Un Artefacto forense puede ser :
Un disco 
Una memoria RAM
Un Registro de Windows
Una Carpeta

SANS Artefactos:
https://github.com/mark-hallman/plaso_filters/blob/master/SANS%20Windows%20Artifact%20Analysis%20Evidence%20Of....pdf

### Montar Evidencia 

![[Pasted image 20260601174211.png]]


![[Pasted image 20260601174752.png]]


### Adquisición de Disco Fisico
![[Pasted image 20260601175102.png]]

![[Pasted image 20260601175209.png]]

RAW es una adquisición Full de las que mas se utiliza y ademas guarda la tabla MFT

E01 Mas comprimida se utiliza mucho en la herramienta Autopsy

Después vienen pestañas de introducción de datos como donde se va a almacenar la adquisición y nombre del examinador nombre de la adquisición etc  

![[Pasted image 20260601175719.png]]

![[Pasted image 20260601175940.png]]


### Montar la Adquisición de Disco que realizamos. Se monta en solo lectura.

![[Pasted image 20260601180824.png]]