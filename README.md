# 🐧 Advanced Linux Server Administration Portfolio
Este repositorio contiene el laboratorio práctico de despliegue, configuración de servicios de red, seguridad y administración avanzada de entornos de servidor basados en sistemas operativos de código abierto.

## 🚀 1. Despliegue y Arquitectura Base de Servidores Linux
Se inició el despliegue de la infraestructura de servidores de la empresa mediante la creación y aprovisionamiento de un entorno virtualizado optimizado para alta disponibilidad:

* **Estrategia Tecnológica:** Se seleccionó la distribución de nivel empresarial **Ubuntu Server 26.04 LTS** bajo la arquitectura de 64 bits para actuar como nodo central de servicios.
* **Optimización de Recursos (SLA):** Al carecer de interfaz gráfica de usuario (GUI), la instancia se configuró de forma altamente eficiente asignando únicamente **2048 MB de memoria RAM**, 2 vCPUs y un disco virtual de **25 GB**, reduciendo drásticamente la huella de almacenamiento frente a estaciones de trabajo tradicionales.
* **Modelo Cliente-Servidor:** La implementación responde a la arquitectura corporativa estándar de TI: se mantiene el parque de estaciones de trabajo bajo plataformas Windows, mientras que la lógica de negocio, bases de datos y seguridad perimetral se consolidan sobre núcleos robustos e independientes de Linux.

## 🛠️ 2. Configuración y Aprovisionamiento del Sistema Base
Durante el despliegue del asistente de instalación por consola, se aplicaron directivas y estándares de nivel corporativo para garantizar la escalabilidad y administración remota del nodo:

* **Arquitectura de Almacenamiento Dinámico (LVM):** Se configuró el disco duro virtual mediante el sistema **LVM (Logical Volume Manager)** sin cifrado. Esta selección es un estándar en infraestructuras IT, ya que permite la expansión o fusión de volúmenes lógicos en caliente y en tiempo real si las necesidades de almacenamiento de la empresa aumentan, evitando paradas de servicio en producción.
* **Identidad de Red (Hostname):** El servidor fue bautizado bajo la nomenclatura corporativa **`srv-linux-01`**, estableciendo su nombre único de resolución de identidad dentro del dominio local de la oficina.
* **Seguridad y Control Remoto (OpenSSH):** Se realizó la instalación obligatoria del demonio **OpenSSH Server (`[X] Install OpenSSH server`)**. Esta configuración es crítica en la administración de sistemas moderna, habilitando al departamento de TI el acceso remoto seguro por consola desde las estaciones de trabajo de soporte, eliminando la necesidad de interacción física directa con el hardware alojado en el CPD (Centro de Procesamiento de Datos).

