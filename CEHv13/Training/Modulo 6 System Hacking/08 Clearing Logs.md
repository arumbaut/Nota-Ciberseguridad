**Clearing Logs**

En la sección anterior, vimos cómo un atacante puede ocultar archivos maliciosos en un equipo objetivo utilizando diversas técnicas de esteganografía, flujos NTFS y otros métodos para mantener el acceso al sistema en el futuro.

Una vez que el atacante ha logrado ejecutar su operación maliciosa, el siguiente paso consiste en eliminar cualquier rastro que pueda delatar su actividad en el sistema.

**Covering Tracks**

El encubrimiento de rastros es una de las etapas clave en el hacking de sistemas. En esta fase, el atacante trata de ocultar su presencia y evitar ser detectado eliminando todas las huellas o logs generados durante su acceso a la red o computadora objetivo.

**Techniques Used for Covering Tracks**

**Disabling Auditing: Auditpol**

**Enabling system auditing:**

C:\>auditpol /set /category:”system”,”account logon” /success:enable /failure:enable

**Disabling system auditing:**

C:\>auditpol /set /category:”system”,”account logon” /success:disable /failure:disable

**Clearing Logs**

Clear_Event_Viewer_Logs.bat is a utility that can be used to wipe out the logs of the target system.

1- Download the Clear_Event_Viewer_Logs.bat utility from https://www.tenforums.com

2- Right-click or press and hold on the .bat file and click/tap on Run as administrator

**Steps to clear PowerShell logs using Clear-EventLog command are as follows.**

**>Clear-EventLog "Windows PowerShell"**

Use the following command to clear specific multiple log types from local or remote systems:

**>Clear-EventLog -LogName ODiag, OSession localhost, Server02**

Use the following command to clear all the logs on the specified systems, and then display the event log list:

**>Clear-EventLog -LogName application, system -confirm**

Steps to clear event logs using wevtutil utility are as follows.

Use the following command to display a list of event logs:

**>wevtutil el**

Use the following command to clear the event logs:

**>wevtutil cl <l**

#### ==**For Linux**==

▪ Navigate to the /var/log directory on the Linux system

▪ Open the plaintext file containing log messages with text editor **/var/log/<filename.log>**

▪ Delete all the log entries logged while compromising the system Module

**Covering BASH Shell Tracks**


**▪ Disabling history**

**export HISTSIZE=0**

**▪ Clearing the history**

**history –c    clearing the stored history**

**history -w    only deletes the history of the current shell**

**Clearing the user’s complete history cat /dev/null**

**> ~/.bash_history && history –c && exit**

**destruye el archivo de historial y hace que su contenido sea ilegible**

**shred ~/.bash_history**

**This command first shreds the history file, then deletes the file, and finally clears all the evidence of its usage.**

**shred ~/.bash_history&& cat /dev/null > ~/.bash_history && history -c && exit**


#### ==**Covering Tracks on a Network**==

**▪ Using Reverse HTTP Shells**

#### Funcionamiento:

 El atacante compromete el sistema y ejecuta un script que hace que el sistema víctima se conecte al servidor HTTP del atacante.
 Una vez establecida la conexión, el atacante puede ejecutar comandos en el sistema comprometido a través de HTTP.

**Delete Files using Cipher.exe**

Cipher.exe es una herramienta de línea de comandos integrada en Windows que se puede utilizar para eliminar datos de manera segura sobrescribiéndolos, evitando así su recuperación en el futuro.

Use the following command to overwrite deleted files in a specific folder:

**cipher /w:\<drive letter\>:\<folder name>**

Use the following command to overwrite all the deleted files in the given drive:

**cipher /w:\<drive letter\>**

Run the following command to display the list of domains recently visited on the browser including the incognito mode browser.

**ipconfig /displaydns**

Now, run the following command in the Command Prompt to clear all DNS cache entries and clear traces of recent browsing history.

**ipconfig /flushdns Figure**

**Attackers can create a hidden user account on the victim system using the following command:**

**net user \<UserName\> /add**

**Run the following command to activate the account for exploitation:**

**net user \<UserName\> /active:yes**

**Run the following command to hide the account when it is not required:**

**net user \<UserName\> /active:no**

**▪ Hiding User Accounts**

Open Registry Editor and navigate to the following location:

**HKEY_LOCAL_MACHINE\Software\Microsoft\WindowsNT\CurrentVersion\Winlogon**

Right click on Winlogon → hover on New → choose Key.