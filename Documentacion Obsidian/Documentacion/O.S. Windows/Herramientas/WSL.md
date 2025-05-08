Los desarrolladores pueden acceder a la potencia de [[WINDOWS]] y [[GNU LINUX]] al mismo tiempo en una máquina Windows. Subsistema de Windows para Linux (WSL) permite a los desarrolladores instalar una distribución de Linux (como Ubuntu, OpenSUSE, Kali, Debian, Arch Linux, etc.) y usar aplicaciones, utilidades y herramientas de línea de comandos de Bash directamente en Windows, sin modificar, sin la sobrecarga de una máquina virtual tradicional o una configuración de arranque dual.
## Comando de Instalación de WSL

Ahora puede instalar todo lo que necesita para ejecutar WSL con un solo comando. Abra [[PowerShell]] o el símbolo del sistema de Windows como **administrador**; para ello, haga clic con el botón derecho y seleccione "Ejecutar como administrador", escriba el comando wsl --install y reinicie la máquina.

Power Shell Copiar

```
wsl --install
```

Este comando habilitará las características necesarias para ejecutar WSL e instalará la distribución Ubuntu de Linux. ([Esta distribución predeterminada se puede cambiar](https://learn.microsoft.com/es-es/windows/wsl/basic-commands#install)).

Si está ejecutando una compilación anterior o simplemente prefiere no usar el comando install y desea instrucciones paso a paso, consulte **[Pasos de instalación manual de WSL para versiones anteriores](https://learn.microsoft.com/es-es/windows/wsl/install-manual)** .

La primera vez que inicie una distribución de Linux recién instalada, se abrirá una ventana de la consola y se le pedirá que espere a que los archivos se descompriman y se almacenen en el equipo. Todos los inicios posteriores deberían tardar menos de un segundo en completarse.
## Cambio de la Distribución Predeterminada de Linux Instalada

De forma predeterminada, la distribución de Linux instalada será Ubuntu. Se puede cambiar mediante la marca `-d`.

- Para cambiar la distribución instalada, escriba: `wsl --install -d <Distribution Name>`. Reemplace `<Distribution Name>` por el nombre de la distribución que desea instalar.
- Para ver una lista de las distribuciones de Linux disponibles para descargar a través de la tienda en línea, escriba `wsl --list --online` o `wsl -l -o`.
- Para instalar distribuciones de Linux adicionales después de la instalación inicial, también puede usar el comando `wsl --install -d <Distribution Name>`.