Un contenedor es un paquete de una aplicación o software que incluye todas sus dependencias, como archivos de biblioteca y configuración, binarios y otros recursos que se ejecutan independientemente de otros procesos en el entorno de nube. Todos estos archivos de recursos se entregan como una unidad para resolver problemas de compatibilidad al migrar aplicaciones entre entornos de nube. Estos contenedores se proporcionan a los suscriptores en forma de CaaS. Un servicio CaaS incluye la virtualización y gestión de contenedores mediante orquestadores. Con estos servicios, los suscriptores pueden desarrollar aplicaciones contenedorizadas completas y escalables en la nube o en centros de datos locales. Hereda características tanto de IaaS como de PaaS. Entre los servicios de contenedores más populares se incluyen Amazon AWS EC2, Google Kubernetes Engine (GKE), Docker, etc.

#### **Features:**
▪ Portability and consistency 
▪ Security 
▪ High efficiency and cost effectiveness 
▪ Scalability
▪ Robustness

#### **Microservicios vs. Docker**
Las aplicaciones monolíticas se dividen en subaplicaciones alojadas en la nube, denominadas microservicios, que funcionan conjuntamente y cada una realiza una tarea única. Los microservicios dividen y distribuyen la carga de trabajo de la aplicación, proporcionando servicios estables, fluidos y escalables al interactuar entre sí. Las aplicaciones monolíticas se descomponen en torno a las capacidades empresariales que permiten a los equipos multifuncionales desarrollar, dar soporte e implementar microservicios. En comparación con los modelos tradicionales de almacenamiento de datos utilizados por las aplicaciones monolíticas, los microservicios descentralizan el almacenamiento de datos al gestionar sus propios almacenes de datos. Los desarrolladores crean un contenedor Docker para cada microservicio. Dado que cada microservicio se empaqueta en el contenedor junto con las bibliotecas, los frameworks y los archivos de configuración necesarios, los microservicios que pertenecen a una misma aplicación pueden desarrollarse y gestionarse mediante múltiples plataformas.


#### **¿Qué es Kubernetes?**
Kubernetes, también conocido como K8s, es una plataforma de orquestación de código abierto, portátil y extensible, desarrollada por Google para la gestión de aplicaciones y microservicios en contenedores. Los contenedores ofrecen una forma eficiente de empaquetar y ejecutar aplicaciones. ==En un entorno de producción en tiempo real, los contenedores deben gestionarse eficientemente para reducir al mínimo el tiempo de inactividad. Por ejemplo, si un contenedor falla, otro se inicia automáticamente. Para solucionar estos problemas, Kubernetes proporciona un marco resiliente para gestionar contenedores distribuidos, generar patrones de implementación y realizar conmutación por error y redundancia para las aplicaciones.==

#### **▪ Types of Cluster Computing** . 

**o Highly Available (HA) or Fail-over:** 
En un clúster de conmutación por error, más de un nodo se ejecuta simultáneamente para ofrecer alta disponibilidad (HA) o disponibilidad continua (CA). Si un nodo falla, el otro asume su responsabilidad con un tiempo de inactividad mínimo o nulo.

**o Load Balancing:** 
En un clúster de balanceo de carga, la carga de trabajo se distribuye entre los nodos para evitar la sobrecarga de un solo nodo. El balanceador de carga realiza comprobaciones periódicas del estado de cada nodo para identificar fallos y redirige el tráfico entrante a otro nodo. Un clúster de balanceo de carga también es un clúster de alta disponibilidad.

**o High-Performance Computing:** 
En un clúster de computación de alto rendimiento (HPC), los nodos se configuran para proporcionar un rendimiento extremo mediante la paralelización de las tareas. El escalado también ayuda a maximizar el rendimiento.