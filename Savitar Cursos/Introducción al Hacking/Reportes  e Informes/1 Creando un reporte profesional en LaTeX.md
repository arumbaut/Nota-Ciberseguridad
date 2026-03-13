- Tags : #reportes #informes #latex

En esta clase aprenderás a usar **LaTeX**, un lenguaje de marcado utilizado para crear documentos científicos y técnicos de alta calidad. A través de ejemplos y ejercicios prácticos, descubrirás cómo utilizar LaTeX para crear documentos bien estructurados, con una apariencia profesional y una alta precisión tipográfica.

Aprenderás a utilizar diversas herramientas y comandos de LaTeX para formatear el texto, insertar figuras y crear tablas. Además, también aprenderás a utilizar paquetes adicionales que te permitirán personalizar aún más tus documentos.

Dos tipos de Informe  **Técnico y Ejecutivo**

Instalamos una serie de utilidades 
```bash
apt update
apt install latexmk zathura
apt install textlive-full

# Para que los pdf los abra con zathura
xdg-mime query default application/pdf
xdg-mime default zathura.desktop application/pdf
 
cd /home/alex/.config
mkdir latexmk
cd latexmk
nano latexmkrc
$pdf_reviewer = "zathura "
```