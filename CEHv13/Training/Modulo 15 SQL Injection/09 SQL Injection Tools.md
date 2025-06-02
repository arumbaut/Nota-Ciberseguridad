#### **▪ sqlmap** Source: https://sqlmap.org

Being an open-source penetration testing tool, sqlmap automates the process of detecting and exploiting SQL injection flaws and taking over database servers.

**▪ Mole** Source: https://sourceforge.net

Mole is an automatic SQL injection exploitation tool. Only by providing a vulnerable URL and a valid string on the site, it can detect the injection and exploit it using the union technique or a Boolean query-based technique.

**▪ jSQL Injection (https://github.com)**

**▪ NoSQLMap (https://github.com)**

**▪ Havij (https://github.com)**

**▪ blind_sql_bitshifting (https://github.com)**

**Discovering SQL Injection Vulnerabilities with AI**

**sudo sgpt --shell “Check for all possible SQL injection on target url http://testphp.vulnweb.com”**

The output of prompt results in the following command:

sqlmap -u "http://testphp.vulnweb.com" --batch --crawl-5 --random-agent --level-5 --risk=3

▪ **-u "http://testphp.vulnweb.com"**: Especifica la URL objetivo a probar.  
▪ **--batch:**  ejecuta sqlmap en modo batch, lo que significa que no pedirá entradas al usuario y usará la configuración predeterminada para todas las solicitudes.  
▪ **--crawl=5:**  habilita el rastreo y visitará hasta 5 niveles de enlaces desde la URL objetivo en un intento de encontrar puntos adicionales de inyección SQL.  
▪ **--random-agent**:  configura un agente de usuario (user agent) aleatorio para cada solicitud HTTP, haciendo que las solicitudes parezcan provenir de diferentes navegadores y reduciendo las posibilidades de detección.  
▪ **--level=5:** Esta opción establece el nivel de pruebas a realizar. Un nivel más alto indica pruebas más exhaustivas. El rango va de 1 a 5.  
▪ **--risk=3**: Esta opción establece el nivel de riesgo de las pruebas a realizar. Un riesgo más alto indica pruebas más agresivas, que podrían interrumpir potencialmente las aplicaciones web. El rango va de 1 a 3.