# Instalación de software libre y propietario

- Estructura de un sistema informático. Monolítica. Jerárquica. Capas o anillos (ring). Máquinas virtuales. Cliente-servidor.
  * https://github.com/jesusninoc/ClasesISO/blob/master/2019-09-17.md#n%C3%BAcleo
  ```PowerShell
  # Mostrar información sobre el núcleo
  [System.Environment]::OSVersion.Version
  wsl uname -r
  ```
  ```PowerShell
  # Mostrar información sobre el núcleo mediante una función
  function mostrarinformacion()
  {
      # Mostrar información sobre el núcleo
      [System.Environment]::OSVersion.Version
      wsl uname -r
  }
  mostrarinformacion
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
    ```PowerShell
    function mostrarcargaprocesador()
    {
        # Mostrar la carga del procesador
        Get-WmiObject win32_processor | Select-Object LoadPercentage
    }
    mostrarcargaprocesador
    ```
  - Administrar la ejecución de los procesos. Planificación.
    * https://www.jesusninoc.com/07/07/7-gestion-de-procesos-en-powershell/
    * https://github.com/jesusninoc/Scripts/blob/master/Ver%20si%20Apache%20est%C3%A1%20encendido.sh
    * https://github.com/jesusninoc/Scripts/blob/master/Ver%20si%20MySQL%20est%C3%A1%20encendido.sh
    * https://github.com/jesusninoc/Scripts/blob/master/Ver%20si%20Apache%20est%C3%A1%20encendido%20y%20enviar%20un%20mail.sh
    * https://github.com/jesnino/Bash/blob/master/Procesos/EjerciciosProcesos.sh
    
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
    ```
    ```PowerShell
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
    ```PowerShell
    # Crear una carpeta con la fecha de hoy que contenga los procesos que se están ejecutando junto con información sobre los hilos (solución mediante funciones)

    function infohilos ($proceso)
    {
        # Valores que necesita: proceso
        # Valores que devuelve: hilos
        (Get-Process -Name $proceso).Threads >> ($proceso+"\informacion.txt")
    }

    $fecha = (Get-Date).ToString("yyyyMMdd")
    mkdir $fecha
    cd $fecha

    foreach($proceso in (Get-Process | select Name -Unique).name)
    {
        $proceso
        mkdir $proceso -force
        infohilos $proceso
    }
    ```
    ```PowerShell
    # Crear una carpeta con la fecha de hoy que contenga los procesos que se están ejecutando junto el número de hilos (solución mediante funciones)

    function contarhilos ($proceso)
    {
        # Valores que necesita: proceso
        # Valores que devuelve: hilos
        (Get-Process -Name $proceso).Threads.Count
    }

    $fecha = (Get-Date).ToString("yyyyMMdd")
    mkdir $fecha
    cd $fecha

    foreach($proceso in (Get-Process | select Name -Unique).name)
    {
        $proceso
        mkdir $proceso -force
        contarhilos $proceso
    }
    ```
    ```PowerShell
    # Arrancar un servicio
    New-Service -Name "Tes2" -BinaryPathName '"C:\Program Files\MySQL\MySQL Server 5.1\bin\mysqld" --defaults-file="C:\Program Files\MySQL\MySQL Server 5.1\my.ini" MySQL'

    Start-Service tes2
    Stop-Service tes2
    ```
    ```Bash
    # Eliminar un proceso o un servicio
    kill -9 `pidof apache2`
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
    * https://github.com/jesusninoc/ClasesISO/blob/master/2019-10-15.md#ver-actualizaciones
    * https://github.com/jesusninoc/ClasesISO/blob/master/2019-10-15.md#obtener-informaci%C3%B3n-sobre-las-actualizaciones
    ```PowerShell
    # Crear carpetas para cada tipo de ProviderName y dentro de cada carpeta meter los paquetes de cada ProviderName
    
    foreach($programa in Get-Package | select ProviderName, name)
    {
        mkdir $programa.ProviderName -Force
        $programa.Name >> ($programa.ProviderName+"\informacion.txt")
    }
    ```
    ```PowerShell
    # Crear carpetas para cada tipo de ProviderName y dentro de cada carpeta meter los paquetes de cada ProviderName (mediante funciones)

    function clasificarporProviderName($programa)
    {
        $programa.Name >> ($programa.ProviderName+"\informacion.txt")
    }

    foreach($programa in Get-Package | select ProviderName, name)
    {
        mkdir $programa.ProviderName -Force
        clasificarporProviderName $programa
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
    * https://github.com/jesusninoc/ClasesISO/blob/master/2018-04-04.md
    * https://github.com/jesusninoc/ClasesISO/blob/master/2019-10-17.md#comandos-para-trabajar-con-discos-en-linux
  - En sistemas Windows determinar la partición donde instalaremos el S.O.
  - En sistemas Linux determinar las particiones para los distintos puntos de montaje.
  - Controladores (drivers) de almacenamiento necesarios.
    * https://github.com/jesusninoc/PowerShell/blob/master/Procesos/EjerciciosProcesosAvanzado.ps1
    * https://github.com/jesusninoc/ClasesISO/blob/master/2019-10-15.md#ver-controladores 
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
  * https://github.com/jesusninoc/ClasesISO/blob/master/2019-10-15.md#instalar-un-paquete-msi-junto-con-informaci%C3%B3n-sobre-la-instalaci%C3%B3n
- Actualización de sistemas operativos y aplicaciones.
  - Actualizar a una versión superior (update).
  - Cambiar a una versión inferior (downgrade).
  - Instalación de parches: de seguridad, funcionales, opcionales, etc.
  - Automatizar las actualizaciones. Configurar la fuente de las actualizaciones.
- Ficheros necesarios para el arranque de los principales sistemas operativos.
- Registros (logs) del sistema.
  - Formato de los registros: fuente/origen, prioridades (informativos, advertencias, errores, etc.)
  - Herramientas para su monitorización en sistemas libres y propietarios.
    * https://www.jesusninoc.com/07/10/10-gestion-del-rendimiento-en-powershell/#Registros_del_sistema
    ```PowerShell
    # Almacenar el número de procesos que se están ejecutando y el número de hilos de cada proceso

    $procesos = gps
    $procesos.count | Out-File log.log -Append

    foreach($proceso in $procesos)
    {
        $proceso.Name | Out-File log.log -Append
        $proceso.threads.Count | Out-File log.log -Append
    }
    ```
    ```PowerShell
    # Almacenar el número de procesos que se están ejecutando y el número de hilos de cada proceso (mediante funciones, cutre)

    function guardarnombre()
    {
        $proceso.Name | Out-File log.log -Append
    }
    function guardarhilos()
    {
        $proceso.threads.Count | Out-File log.log -Append
    }

    $procesos = gps
    $procesos.count | Out-File log.log -Append

    foreach($proceso in $procesos)
    {
        guardarnombre
        guardarhilos
    }
    ```
    ```PowerShell
    # Almacenar el número de procesos que se están ejecutando y el número de hilos de cada proceso (mediante funciones)

    function guardarnombre($proceso)
    {
        $proceso.Name | Out-File log.log -Append
    }
    function guardarhilos($proceso)
    {
        $proceso.threads.Count | Out-File log.log -Append
    }

    $procesos = gps
    $procesos.count | Out-File log.log -Append

    foreach($proceso in $procesos)
    {
        guardarnombre $proceso
        guardarhilos $proceso
    }
    ```
  - Gestión: Aplicar filtros, asociar tareas en respuesta a ciertos eventos, etc.
- Actualización y mantenimiento de controladores de dispositivos.
  - Automatizar la actualización de controladores.
  - Volver a una versión anterior de un controlador.
  - Actualización manual de los controladores.

# Administración y aseguramiento de la información
- Sistemas de archivos:
  - Propietarios y libres.
  - Rutas y nombres de archivos. Estructura jerárquica.
    * https://www.jesusninoc.com/07/04/4-gestion-del-sistema-de-archivos-en-powershell/#La_ruta
- Gestión de sistemas de archivos mediante comandos y entornos gráficos.
- Gestión de enlaces.
- Estructura de directorios de sistemas operativos libres y propietarios.
- Búsqueda de información del sistema mediante comandos y herramientas gráficas.
  * https://github.com/jesusninoc/Bash/blob/master/Ficheros/EjerciciosFicherosBuscar.sh
- Identificación del software instalado mediante comandos y herramientas gráficas.
  * https://www.jesusninoc.com/07/05/5-gestion-del-software-en-powershell/
- Gestión de la información del sistema. Rendimiento. Estadísticas.
- Montaje y desmontaje de dispositivos en sistemas operativos. Automatización.
  * https://www.jesusninoc.com/07/04/4-gestion-del-sistema-de-archivos-en-powershell/#Discos
- En sistemas Windows montar un volumen en una o más carpetas.
  * https://www.jesusninoc.com/07/04/4-gestion-del-sistema-de-archivos-en-powershell/#Montar_un_disco_virtual
- Herramientas de administración de discos. Particiones y volúmenes. Desfragmentación y chequeo.
- Permisos locales de acceso a ficheros y directorios.
  * https://github.com/jesusninoc/ClasesISO/blob/master/2019-11-05.md#permisos-en-linux
  * https://github.com/jesusninoc/ClasesISO/blob/master/2019-11-07.md#permisos-en-linux
  * https://www.jesusninoc.com/07/04/4-gestion-del-sistema-de-archivos-en-powershell/#Permisos-2
  * https://github.com/jesusninoc/ClasesSOM/blob/master/2018-11-26.md
  * https://github.com/jesusninoc/ClasesSOM/blob/master/2018-11-27.md
  * https://www.jesusninoc.com/03/30/eliminar-permisos-explicitos/
