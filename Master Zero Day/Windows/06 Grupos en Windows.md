Cada Windows tiene grupos locales predeterminados. Los más importantes:

**Administrators: Control total del sistema**
- Pueden hacer cualquier cosa    
- Instalar software, cambiar configuración, acceder a todo
    
**Users: Usuarios estándar**
- No pueden instalar software que afecte a todo el sistema    
- Pueden ejecutar aplicaciones ya instaladas    
- Tienen su perfil de usuario con permisos sobre sus propios archivos

**GRUPOS EN AD**

En AD hay tres tipos de grupos:
**Security Groups: Se usan para asignar permisos**
- Domain Admins    
- Domain Users    
- Enterprise Admins    
- Schema Admins    

**Distribution Groups:**
- Solo para listas de distribución de email    

**Ámbitos de grupo:**
- **Domain Local:** Solo en el dominio donde se crea    
- **Global:** Puede usarse en cualquier dominio del bosque    
- **Universal:** Para múltiples dominios

Obtener los grupos 
```
Muestra todos
net localgroup

Mustra los users en el grupo Administradores
net localgroup Administradores
```

Windows controla el acceso a archivos y carpetas mediante los **permisos**. Aquí hay dos sistemas de permisos que se superponen:

- **Permisos NTFS:** Controlan el acceso al sistema de archivos a nivel local    
- **Permisos de recursos compartidos (SMB):** Controlan el acceso cuando accedes a una carpeta por la red

**¿Qué son los permisos NTFS?**

- **NTFS (New Technology File System)** es el sistema de archivos moderno de Windows. A diferencia de FAT32, NTFS soporta permisos granulares sobre archivos y carpetas.    
- Cada archivo y carpeta en NTFS tiene una **ACL (Access Control List)** que define quién puede hacer qué.    

**Permisos básicos**

- **Full Control:** Control total: leer, escribir, modificar permisos, tomar posesión, eliminar.    
- **Modify:** Leer, escribir, ejecutar, eliminar archivos/subcarpetas.    
- **Read & Execute:** Ver contenido, ejecutar programas, recorrer carpetas.    
- **List Folder Contents:** Ver nombres de archivos y subcarpetas (solo para carpetas).    
- **Read:** Ver contenido de archivos, propiedades, permisos.    
- **Write:** Crear archivos/carpetas nuevos, modificar atributos.