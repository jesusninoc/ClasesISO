# Instalación de software libre y propietario

- Estructura de un sistema informático. Monolítica. Jerárquica. Capas o anillos (ring). Máquinas virtuales. Cliente-servidor.
  * https://github.com/jesusninoc/ClasesISO/blob/master/2019-09-17.md#n%C3%BAcleo
  ```PowerShell
  # Mostrar información sobre el núcleo
  Get-CimInstance Win32_OperatingSystem | select SerialNumber
  [System.Environment]::OSVersion.Version
  wsl uname -r
  ```
- Arquitectura de un sistema operativo. Sistemas por lotes (batch). Sistemas por lotes con multiprogramación. Sistemas de tiempo compartido. Sistemas distribuidos.
  * https://www.jesusninoc.com/07/03/3-gestion-del-hardware-en-powershell/#Procesador
- Funciones de un sistema operativo.
  - Controlar y gestionar el uso del hardware del ordenador: CPU, dispositivos de E/S, Memoria principal, tarjetas gráficas y el resto de periféricos.
    * https://www.jesusninoc.com/07/03/3-gestion-del-hardware-en-powershell
    ```PowerShell
    # Mostrar la carga del procesador
     Get-WmiObject win32_processor | Select-Object LoadPercentage
    ```
  - Administrar la ejecución de los procesos. Planificación.
    * https://www.jesusninoc.com/07/07/7-gestion-de-procesos-en-powershell/
    ```PowerShell
    # Crear una carpeta con la fecha de hoy que contenga los procesos que se están ejecutando junto con información sobre los hilos (solución 1)

    $fecha = (Get-Date).ToString("yyyyMMdd")
    mkdir $fecha
    cd $fecha

    mkdir (Get-Process | select Name -Unique).name

    foreach($carpeta in (Get-ChildItem).Name)
    {
        $carpeta
        (Get-Process -Name $carpeta).Threads >> ($carpeta+"\informacion.txt")
    }
    
    # Crear una carpeta con la fecha de hoy que contenga los procesos que se están ejecutando junto con información sobre los hilos (solución 2)

    $fecha = (Get-Date).ToString("yyyyMMdd")
    mkdir $fecha
    cd $fecha

    foreach($carpeta in (Get-Process | select Name -Unique).name)
    {
        $carpeta
        mkdir $carpeta
        (Get-Process -Name $carpeta).Threads >> ($carpeta+"\informacion.txt")
    }
    ```
  - Controlar el proceso de organización de la información. Creación, acceso (ubicación física) y borrado de archivos.
    * https://www.jesusninoc.com/07/04/4-gestion-del-sistema-de-archivos-en-powershell/#Archivos
  - Controlar el acceso de los programas o los usuarios a los recursos del sistema.
  ```Bash
  ps -U root -u root u
  ps -eo user,comm
  ```
  - Proporcionar interfaces de usuario: en modo texto y gráficos.
  - Servicios soporte: actualizaciones de software, controladores para nuevos periféricos, etc.
    * https://www.jesusninoc.com/07/05/5-gestion-del-software-en-powershell/#Actualizaciones
    * https://www.jesusninoc.com/07/07/7-gestion-de-procesos-en-powershell/
    ```PowerShell
    # Crear carpetas para cada tipo de ProviderName y dentro de cada carpeta meter los paquetes de cada ProviderName
    
    foreach($programa in Get-Package | select ProviderName, name)
    {
        mkdir $programa.ProviderName -Force
        $programa.Name >> ($programa.ProviderName+"\informacion.txt")
    }
    ```
- Tipos de sistemas operativos.
  - Monousuario o multiusuario
  - Centralizado o distribuido
  - Monotarea o multitarea
  - Uniprocesador o multiprocesador
  - Instalables y/o autoarrancables.
- Sistemas operativos libres.
- Sistemas operativos propietarios.
- Tipos de aplicaciones. Software de sistema. Software de programación. Software de aplicación.
- Licencias y tipos de licencias. Según los derechos que cada autor se reserva sobre su obra. Según su destinatario.
- Máquinas virtuales (M.V.)
  - Concepto de virtualización del hardware y características de los principales productos software libre y propietario, para el uso de máquinas virtuales.
  - Creación y personalización de M.V.
  - Ventajas e inconvenientes de la virtualización.
- Consideraciones previas a la instalación de sistemas operativos libres y propietarios.
  - Particionado del disco duro.
    * https://github.com/jesusninoc/ClasesISO/blob/master/2019-10-17.md#comandos-para-trabajar-con-discos-en-linux
  - En sistemas Windows determinar la partición donde instalaremos el S.O.
  - En sistemas Linux determinar las particiones para los distintos puntos de montaje.
  - Controladores (drivers) de almacenamiento necesarios.
    * https://github.com/jesusninoc/PowerShell/blob/master/Procesos/EjerciciosProcesosAvanzado.ps1
- Instalación de sistemas operativos.
  - Requisitos hardware, versiones y licencias.
    * https://www.jesusninoc.com/07/03/3-gestion-del-hardware-en-powershell/
    * https://github.com/jesusninoc/ClasesISO/blob/master/2017-10-12.md
    * https://github.com/jesusninoc/PowerShell/blob/master/Hardware/EjemplosHardware.ps1
    * https://github.com/jesusninoc/PowerShell/blob/master/Hardware/EjemplosHardware2.ps1
    * https://github.com/jesusninoc/ClasesISO/blob/master/2019-11-20.md#1-realizar-un-inventario-de-tu-equipo-a-nivel-hardware-y-software-ten-en-cuenta-c%C3%B3mo-clasificar-la-informaci%C3%B3n-y-no-olvides-temas-importantes-como-por-ejemplo-controladores
  - Soporte utilizado para la instalación: CD/DVD, Pendrive, LAN.
  - Datos necesarios para la instalación: usuarios, contraseñas, nombre del equipo, direcciones IP, número de licencia, etc.
- Gestión de varios sistemas operativos en un ordenador.
  - Requisitos previos. Administración del espacio del disco. Particionado y redimensionado.
  - Problemas con el registro maestro de arranque (MBR). Elegir un gestor de arranque compatible con todos los sistemas operativos a instalar.
  - Preparar las particiones de los S.O. para permitir su arranque.
  - Analizar el orden en la instalación de los sistemas operativos.
- Gestores de arranque.
  - Código de arranque maestro (Master Boot Code).
  - Formatos tabla de particiones. Master Boot Record (MBR) y Guid Partition Table (GPT).
  - Configuración de los gestores de arranque de los sistemas operativos libres y propietarios.
  - Reparación del gestor de arranque.
  - Sustitución del gestor de arranque estándar por otro más completo.
- Instalación/desinstalación de aplicaciones. Requisitos hardware y software, versiones y licencias.
- Actualización de sistemas operativos y aplicaciones.
  - Actualizar a una versión superior (update).
  - Cambiar a una versión inferior (downgrade).
  - Instalación de parches: de seguridad, funcionales, opcionales, etc.
  - Automatizar las actualizaciones. Configurar la fuente de las actualizaciones.
- Ficheros necesarios para el arranque de los principales sistemas operativos.
- Registros (logs) del sistema.
  - Formato de los registros: fuente/origen, prioridades (informativos, advertencias, errores, etc.)
  - Herramientas para su monitorización en sistemas libres y propietarios.
  - Gestión: Aplicar filtros, asociar tareas en respuesta a ciertos eventos, etc.
- Actualización y mantenimiento de controladores de dispositivos.
  - Automatizar la actualización de controladores.
  - Volver a una versión anterior de un controlador.
  - Actualización manual de los controladores.

# Administración y aseguramiento de la información
- Sistemas de archivos:
  - Propietarios y libres.
  - Rutas y nombres de archivos. Estructura jerárquica.
- Gestión de sistemas de archivos mediante comandos y entornos gráficos.
- Gestión de enlaces.
- Estructura de directorios de sistemas operativos libres y propietarios.
- Búsqueda de información del sistema mediante comandos y herramientas gráficas.
- Identificación del software instalado mediante comandos y herramientas gráficas.
- Gestión de la información del sistema. Rendimiento. Estadísticas.
- Montaje y desmontaje de dispositivos en sistemas operativos. Automatización.
- En sistemas Windows montar un volumen en una o más carpetas.
- Herramientas de administración de discos. Particiones y volúmenes. Desfragmentación y chequeo.
- Permisos locales de acceso a ficheros y directorios.

---------------------

# Realizar script de tareas básicas
* https://github.com/jesusninoc/Scripts/blob/master/Realizar%20tareas%20b%C3%A1sicas%20y%20avanzadas.sh

# Repaso de scripting
* https://www.jesusninoc.com/07/01/1-introduccion-a-powershell/
* https://www.jesusninoc.com/07/02/2-programacion-en-powershell/
* https://www.jesusninoc.com/07/03/3-gestion-del-hardware-en-powershell/
* https://www.jesusninoc.com/07/04/4-gestion-del-sistema-de-archivos-en-powershell/
* https://www.jesusninoc.com/07/05/5-gestion-del-software-en-powershell/
* https://www.jesusninoc.com/07/07/7-gestion-de-procesos-en-powershell/
* https://www.jesusninoc.com/07/10/10-gestion-del-rendimiento-en-powershell/

# Funciones en PowerShell
* https://github.com/jesusninoc/ClasesISO/blob/master/2019-11-12.md#funciones-en-powershell

---------------------

# Ejercicios propuestos (Bash, PowerShell y WSL)

- Arrancar un proceso o un servicio
  * https://www.jesusninoc.com/2017/10/17/crear-un-servicio-en-windows-con-powershell/
```PowerShell
New-Service -Name "Tes2" -BinaryPathName '"C:\Program Files\MySQL\MySQL Server 5.1\bin\mysqld" --defaults-file="C:\Program Files\MySQL\MySQL Server 5.1\my.ini" MySQL'

Start-Service tes2
Stop-Service tes2
```
- Eliminar un proceso o un servicio
  * https://github.com/jesnino/Bash/blob/master/Procesos/EjerciciosProcesos.sh
```Bash
kill -9 `pidof apache2`
```
- Indicar si se está ejecutando o no un proceso
  * https://github.com/jesusninoc/Scripts/blob/master/Ver%20si%20Apache%20est%C3%A1%20encendido.sh
  * https://github.com/jesusninoc/Scripts/blob/master/Ver%20si%20MySQL%20est%C3%A1%20encendido.sh
  * https://github.com/jesusninoc/Scripts/blob/master/Ver%20si%20Apache%20est%C3%A1%20encendido%20y%20enviar%20un%20mail.sh
