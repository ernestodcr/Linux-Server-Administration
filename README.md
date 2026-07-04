# 🐧 Linux Server Administration
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

## 🔐 6. Fase 11: Seguridad, Permisos Avanzados y Traspaso de Propiedad (chmod / chown)
Se auditó y corrigió una vulnerabilidad de exposición de datos en el sistema de archivos del servidor, aplicando directivas estrictas de control de accesos bajo el estándar de privilegios mínimos:

* **Traspaso de Propiedad Orgánica (`chown`):** Mediante la directiva avanzada `sudo chown contable1:contabilidad informe_contabilidad.txt`, se retiraron los derechos de propiedad al equipo de soporte y se asignó formalmente el fichero al usuario legítimo (`contable1`) junto con su grupo departamental (`contabilidad`).
* **Modificación de Máscara de Permisos Octal (`chmod`):** Se erradicó el acceso de lectura al resto del mundo aplicando la máscara restrictiva `sudo chmod 660 informe_contabilidad.txt`. Esta configuración reescribió los bits de control pasándolos de `-rw-rw-r--` a `-rw-rw----`.
* **Resultado del Blindaje:** El propietario y los miembros del departamento financiero consolidan permisos de lectura y modificación del informe (`rw-`), mientras que cualquier otro usuario no autorizado del servidor queda completamente bloqueado frente a flujos de lectura o manipulación.

## 🧹 7. Comandos de Mantenimiento Avanzado y Ciclo de Vida de Ficheros (cp / mv / rm)
Se ejecutaron operaciones esenciales de mantenimiento de almacenamiento y gestión de datos, asimilando el comportamiento del sistema operativo ante duplicaciones con elevación de privilegios y borrados definitivos:

* **Duplicación Segura (`cp`):** Tras validar el aislamiento del fichero original, se utilizó la directiva `sudo cp informe_contabilidad.txt copia_seguridad.txt`. Al invocar privilegios administrativos, el nuevo fichero heredó de forma lógica la propiedad del usuario raíz (`root:root`).
* **Reubicación de Volúmenes (`mv`):** Se aprovisionó una estructura dedicada mediante `mkdir backup` y se procedió a reubicar el respaldo utilizando el comando `sudo mv copia_seguridad.txt backup/`, aislando la copia del directorio de producción sin alterar sus metadatos ni permisos de origen.
* **Destrucción Permanente de Datos (`rm`):** Se simuló la obsolescencia de los datos ejecutando la orden irreversible `sudo rm backup/copia_seguridad.txt`. Al carecer de entorno gráfico con papelera de reciclaje, el sistema liberó los bloques de almacenamiento en disco de forma inmediata, consolidando una limpieza absoluta auditada mediante `total 0`.

## 📉 8. Monitorización de Rendimiento y Análisis de Almacenamiento (top / df / free)
Se establecieron las metodologías de soporte de nivel avanzado para auditar los signos vitales, el rendimiento del hardware y la capacidad de almacenamiento del nodo en tiempo real:

* **Administración de Procesos Activos (`top`):** Se implementó el monitor dinámico interactivo para auditar el consumo porcentual de CPU, la asignación de memoria e identificar los identificadores de procesos (PID) con mayor demanda de recursos en producción.
* **Auditoría de Almacenamiento Estándar (`df -h`):** Se ejecutó el comando de análisis de disco bajo formato legible para humanos, localizando con éxito la partición base del Kernel (`/dev/sda2` en `/boot`) y el volumen lógico dinámico raíz (`/dev/mapper/ubuntu--vg-ubuntu--lv` sobre `/`), controlando los umbrales de ocupación (49% actual).
* **Control de Memoria Volátil (`free -m`):** Se asimiló el comando de diagnóstico rápido para obtener un volcado instantáneo en Megabytes de la memoria RAM física activa, segmentando el espacio libre disponible frente a los búferes de intercambio (*Swap*) del servidor.

## 📡 9. Gestión de Paquetes e Instalación de Software Avanzado (apt / htop)
Se procedió a implementar la administración y aprovisionamiento de software del servidor conectando el nodo con los repositorios oficiales de la distribución en internet, optimizando el entorno con herramientas avanzadas de diagnóstico:

* **Sincronización de Repositorios (`apt update`):** Se utilizó la directiva con privilegios elevados `sudo apt update` para descargar los índices y metadatos de paquetes más modernos desde los servidores espejo de España. Esta acción actualiza el catálogo interno de dependencias garantizando la posterior instalación de parches ciberseguros.
* **Aprovisionamiento Automatizado (`apt install`):** Se ejecutó la instalación de software mediante la orden `sudo apt install -y htop`. El parámetro `-y` optimizó el despliegue forzando la aceptación de consumo de disco por adelantado sin requerir pausas interactivas.
* **Monitorización Vitaminada (`htop`):** Se desplegó la herramienta gráfica interactiva `htop`, sustituyendo al clásico monitor plano `top`. Este panel permite auditar a todo color el rendimiento segmentado de las 2 vCPUs, la huella exacta en Megabytes de la memoria RAM activa y la gestión interactiva de los identificadores de procesos (PID).

## 📡 10. Configuración de Red Estática Empresarial (Netplan)
Se configuró el servidor para usar una dirección IP fija en lugar de una automática, garantizando que el equipo sea localizable siempre en el mismo punto de la red local:

* **Archivo de Configuración (`/etc/netplan`):** Se editó el fichero `00-installer-config.yaml` desactivando el protocolo automático (DHCP) e introduciendo manualmente la IP fija del servidor, la puerta de enlace del router y los servidores DNS.
* **Aplicación y Control (`netplan apply`):** Se ejecutó el comando de refresco de red para activar las nuevas reglas en la tarjeta de interfaz de red, validando el éxito del direccionamiento mediante un test de conectividad externa con resultado óptimo.

## 🔄 11. Control de Servicios y Demonios del Sistema (Systemctl)
Se aprendió a controlar los programas invisibles que se ejecutan en segundo plano en el servidor, asegurando que las herramientas críticas estén operativas:

* **Gestión del Demonio SSH (`systemctl`):** Se utilizó la herramienta de control para auditar el estado del servidor OpenSSH. Tras detectar que el software se encontraba inactivo por defecto (`inactive`), se forzó su encendido manual mediante la directiva `sudo systemctl start ssh`.
* **Validación de Estado Operativo:** Se comprobó con éxito la activación del servicio mediante el reporte gráfico verde `active (running)`, dejando el canal de comunicaciones listo para recibir conexiones remotas en la infraestructura.

## 🖥️ 12. Conexión Remota Segura desde el Equipo Real (SSH / Port Forwarding)
Se consolidó el hito de administración remota de la infraestructura, logrando gobernar el servidor Linux a distancia desde la consola de comandos de Windows sin interactuar con el hipervisor:

* **Túnel de Reenvío de Puertos:** Ante el aislamiento de la Red NAT, se configuró una regla de Port Forwarding en VirtualBox, enlazando el puerto libre `2222` de la máquina real (Anfitrión) con el puerto estándar `22` del servidor (Invitado).
* **Acceso SSH Exitoso (`localhost`):** Se ejecutó la conexión remota desde el símbolo del sistema de Windows mediante la directiva `ssh -p 2222 soporte-it@127.0.0.1`. Se aceptó la huella de seguridad criptográfica y se validaron las credenciales corporativas, tomando el control total del nodo a través de la red local.












