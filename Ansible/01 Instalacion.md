Para instalar Ansible utilizando **pip** (el gestor de paquetes de Python) en tu computadora, sigue estos pasos basados en las fuentes:

1. Asegúrate de tener Python 3

Se recomienda encarecidamente utilizar **Python 3**, ya que Python 2 ha sido deprecado.

- Si estás en un **Mac**, puedes instalar Python 3 a través de Homebrew con el comando `brew install python3`.
- Si estás en **Windows**, la recomendación es utilizar el **Subsistema de Windows para Linux (WSL)**. Dentro de este entorno Linux, es posible que primero debas instalar el paquete de pip usando el gestor de paquetes del sistema (por ejemplo, `sudo apt install python3-pip` en sistemas basados en Ubuntu/Debian).

2. Ejecuta el comando de instalación

Una vez que tengas Python y pip configurados, ejecuta el siguiente comando en tu terminal:

```
pip3 install ansible
```

En Ubuntu 
```
sudo apt install ansible
```

Este comando descargará e instalará el conjunto completo de herramientas de Ansible, incluyendo los comandos `ansible`, `ansible-playbook`, herramientas de gestión de inventario y documentación, junto con todas las librerías de las que depende.

3. Consideraciones importantes

- **Permisos:** A veces, la versión de Python integrada en tu computadora puede dar problemas de permisos. Aunque podrías sentirte tentado a usar `sudo pip install ansible`, las fuentes sugieren tener cuidado, ya que esto puede complicar la gestión del entorno de Python.
- **Tiempo de instalación:** La primera vez que realices la instalación, puede tardar unos minutos en descargar todos los paquetes necesarios.

4. Verifica la instalación

Para confirmar que Ansible se instaló correctamente y ver qué versión estás utilizando, ejecuta:

```
ansible --version
```

Este comando te mostrará información sobre la ubicación del ejecutable y la versión de Python que Ansible está detectando

## Ansible repo de ejercicios iniciales.

https://github.com/geerlingguy/ansible-for-devops/tree/master/first-ansible-playbook