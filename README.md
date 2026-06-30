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

---

## 📂 3. Estructura de Directorios Estándar (FHS) y Comandos de Navegación
Se procedió a realizar una auditoría de reconocimiento sobre el árbol de almacenamiento base del servidor, validando la jerarquía de ficheros estándar en sistemas GNU/Linux y asimilando los comandos esenciales de control de terminal:

* **Control de Ubicación y Listado:** Se implementaron los comandos nucleares **`pwd`** (*Print Working Directory*) para monitorizar de forma exacta la ruta absoluta actual en disco, y **`ls`** junto con su modificador avanzado **`ls -la`** para auditar atributos detallados, permisos, marcas de tiempo y ficheros ocultos del entorno.
* **Técnicas de Desplazamiento:** Se dominó el uso de **`cd ..`** para realizar una regresión hacia directorios padre, y el atajo de teletransporte global **`cd`** (a secas) para forzar un retorno inmediato hacia el directorio "home" personal (`~`), optimizando los tiempos de respuesta en consola.
* **Mapeo del Núcleo del Servidor (`/`):** Se mapearon los directorios más críticos del estándar FHS para la gestión empresarial:
  * `/etc`: Repositorio neurálgico que aloja los ficheros de configuración globales del sistema y demonios de red (ej. SSH, interfaces).
  * `/var`: Destinado a almacenar información de tamaño altamente mutable, albergando registros de eventos (*logs*) críticos del servidor y bases de datos corporativas.
  * `/bin` y `/sbin`: Directorios binarios que consolidan las herramientas y comandos esenciales ejecutables del propio sistema operativo.
  * `/boot`: Almacén que custodia los archivos estáticos de carga y el núcleo (*Kernel*) indispensable para el arranque del hardware.

---

## 📝 4. Gestión de Archivos, Creación de Directorios y Edición por Consola
Se procedió a simular un escenario de estructuración de datos corporativos dentro del entorno del servidor, adquiriendo destreza en el aprovisionamiento de carpetas y la manipulación de flujos de texto sin interfaz gráfica:

* **Aprovisionamiento de Estructuras (`mkdir`):** Se utilizó el comando **`mkdir datos_empresa`** dentro del entorno del Home de usuario (`~`) para generar un contenedor lógico aislado destinado a albergar la documentación de los departamentos.
* **Edición de Ficheros en Caliente (`nano`):** Se dominó el uso del editor integrado **GNU Nano** mediante el comando `nano informe_contabilidad.txt`, asimilando las directivas de control por teclado (`Ctrl+O` para la persistencia de datos en disco y `Ctrl+X` para la interrupción/salida segura del editor).
* **Volcado de Flujos por Terminal (`cat`):** Se implementó el comando **`cat`** para realizar lecturas rápidas de la carga útil del fichero directamente sobre la salida estándar de la consola, optimizando las auditorías de contenido sin necesidad de invocar editores interactivos.

## 👥 5. Gestión de Usuarios y Grupos (Identidades Corporativas)
Se implementó la estructura de personal de la empresa dentro del servidor, aplicando políticas de organización departamental y blindaje de credenciales mediante el uso de la terminal de comandos:

* **Creación del Departamento (`groupadd`):** Se utilizó la directiva con privilegios elevados **`sudo groupadd contabilidad`** para fundar el grupo lógico destinado al personal financiero.
* **Aprovisionamiento del Empleado (`useradd`):** Se dio de alta al usuario **`contable1`** mediante el comando avanzado **`sudo useradd -m -g contabilidad contable1`**. El parámetro `-m` forzó la creación automatizada de su directorio de trabajo independiente (`/home/contable1`) y la bandera `-g` consolidó su adscripción inmediata al grupo departamental principal.
* **Seguridad de Credenciales (`passwd`):** Se fijó el entorno criptográfico de autenticación mediante el comando **`sudo passwd contable1`**, asegurando que la cuenta nazca activa y protegida bajo contraseña.
* **Auditoría de Identidades (`id`):** Se ejecutó el comando de control **`id contable1`** para validar la consistencia en los identificadores de seguridad (UID/GID), ratificando la integración total del usuario en el sistema.




