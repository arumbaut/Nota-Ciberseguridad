- Tags: #forense #herramientas_forenses #herramientas_adquisicion #herramientas_montaje #herramientas_analisis_evidencia 


# Adquisición

### Windows

**FTK Imagen**: Herramienta para #window permite la adquisición y análisis de dispositivos de almacenamiento sin alterar los datos originales.
*Link*: [https://www.exterro.com/digital-forensics-software/ftk-imager](https://www.exterro.com/digital-forensics-software/ftk-imager)
*Funcionalidades*
- Permite la creación de imágenes exactas de discos duros y dispositivos de almacenamiento USB , tarjetas de memorias , smartphones, tables, CD, DVD, Blue Ray
- Exportación de evidencias digitales sin alterar la evidencia original
- Verification de hash para la integridad

**WINHEX**  
*Link*:[https://x-ways.net/winhex/](https://x-ways.net/winhex/)

**DISC2 VHD**: Viene preinstalada en Windows, no es mas que el administrador de discos

### Linux
**DD**: Comando de **Linux** que nos permite crear imágenes de discos bit  a bit haciendo copias exactas.
**GUYMAGER**: Para SO Linux se le conoce como el *FTK Imagen* de los *SO UNIX*. Cuenta con una Interface de Usuario ademas de generar informes y soporta el hasing
# Análisis
**FTK Imagen**:
**GUYMAGER**
# Montaje
### Window:
**FTK Imagen**: Permite el montaje de imágenes de disco como una unidad virtual en nuestro sistema operativo proporcionando acceso a los archivos y carpetas.  

**OSFMOUNT**: Herramienta gratuita que permite montar imágenes de disco en windows como discos virtuales
*Link*: [https://www.osforensics.com/tools/mount-disk-images.html](https://www.osforensics.com/tools/mount-disk-images.html)

**ARSENAL IMAGE MOUNTER**: Para Windows. Monta las imágenes como si fueran discos reales físicos. *Esto nos sirve si estamos utilizando un software de análisis que requiera que los discos sean físicos*
*Link*: [https://arsenalrecon.com/products/arsenal-image-mounter](https://arsenalrecon.com/products/arsenal-image-mounter)
### Linux
**EWF TOOLS**:


# Adquisición de evidencias digitales

**AUTOPSY** : Funciona tanto para #linux como para #windows, ofrece interface gráfica de usuario para el análisis de discos duros y smartphones. Analiza automáticamente 
*Link*: [https://www.autopsy.com/download/](https://www.autopsy.com/download/)
#### Funcione:
Análisis de archivos , carpetas , recuperación de archivos borrados, revisión de registros del sistema, análisis de memoria *RAM* etc.

**SLEUTH KIT**: Herramienta de linea de comando para sistemas UNIX y windows, *ATOPSY* proporciona una interface gráfica para *SLEUTH KIT* facilitando su uso.
#### Funcione:
Análisis de archivos , carpetas , recuperación de archivos borrados, revisión de registros del sistema, análisis de memoria *RAM* etc.

**VOLATILITY**: Herramienta numero 1 en el análisis de memoria RAM o volátil. Soporta cualquier análisis de volcado de memoria tanto en #window como en #linux #mac #android