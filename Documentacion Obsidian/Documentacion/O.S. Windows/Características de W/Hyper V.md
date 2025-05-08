Ya sea un desarrollador de software, un profesional de TI o un entusiasta de la tecnología, muchos de ustedes necesitan ejecutar varios [[Sistemas Operativos]]. Hyper-V le permite ejecutar varios sistemas operativos como [[máquinas virtuales]] en [[WINDOWS]].
## Motivos para Usar la Virtualización

La virtualización le permite:

- Ejecutar software que requiera versiones anteriores de sistemas operativos Windows o que no sean Windows.
    
- Experimentar con otros sistemas operativos. Hyper-V facilita la creación y eliminación de diferentes sistemas operativos.
    
- Pruebe el software en varios sistemas operativos mediante varias máquinas virtuales. Con Hyper-V, puede ejecutarlos todos en un solo equipo de escritorio o portátil. Estas máquinas virtuales se pueden exportar y luego importar en cualquier otro sistema de Hyper-V, incluido Azure.
## Requisitos del Sistema
Hyper-V requiere:

Un procesador de 64 bits con funcionalidades de traducción de direcciones de segundo nivel (SLAT).

Windows 10 (Pro o Enterprise) o Windows 11 (Pro o Enterprise)

Para actualizar a Windows Pro, abra Configuración>Actualización y seguridad>Activación. Aquí puede visitar la tienda y comprar una actualización.

La mayoría de los equipos ejecutan Hyper-V; sin embargo, cada máquina virtual ejecuta un sistema operativo totalmente distinto. Por lo general, puede ejecutar una o varias máquinas virtuales en un equipo con 4 GB de RAM, aunque necesitará más recursos para máquinas virtuales adicionales o para instalar y ejecutar software que consume muchos recursos, como juegos, aplicaciones de edición de vídeo o software de diseño de ingeniería.

Para obtener más información sobre los requisitos del sistema de Hyper-V y cómo comprobar que Hyper-V se ejecuta en la máquina, consulte la Referencia de requisitos de Hyper-V.

## Sistemas Operativos que se Pueden Ejecutar en una Máquina Virtual

Hyper-V en Windows admite muchos sistemas operativos diferentes en las máquinas virtuales, incluyendo diversas versiones de Linux, FreeBSD y Windows.

Como recordatorio, debe tener una licencia válida de los sistemas operativos que use en las máquinas virtuales.

Para obtener información sobre los sistemas operativos que se admiten como invitados en Hyper-V en Windows, consulte Sistemas operativos invitados de Windows admitidos y Sistemas operativos invitados de Linux compatibles.

Diferencias entre Hyper-V en Windows y Hyper-V en Windows Server
Existen algunas características que funcionan de forma diferente en Hyper-V en Windows que en Hyper-V en Windows Server.

Funciones de Hyper-V disponibles solo en Windows Server:

- Migración en vivo de máquinas virtuales de un host a otro.
- Réplica de Hyper-V.
- Canal de fibra virtual.
- Redes de SR-IOV.
- .VHDX compartido.

Funciones de Hyper-V disponibles solo en Windows:

- Creación rápida y galería de VM
- Red predeterminada (conmutador NAT)

El modelo de administración de memoria es diferente en Hyper-V en Windows. En un servidor, la memoria de Hyper-V se administra presuponiendo que solo las máquinas virtuales se ejecutan en el servidor. En Hyper-V en Windows, la memoria se administra teniendo en cuenta que la mayoría de las máquinas cliente ejecutan software en el host además de ejecutar máquinas virtuales.
## Limitaciones

Los programas que dependan de un hardware concreto no funcionarán bien en una máquina virtual. Por ejemplo, los juegos o aplicaciones que requieren procesamiento con GPU podrían no funcionar bien. Además, las aplicaciones que dependen de temporizadores de menos de 10 ms, como las aplicaciones de mezcla de música en vivo o las que requieren alta precisión en los tiempos, podrían tener problemas al ejecutarse en una máquina virtual.

Además, si tiene habilitado Hyper-V, esas aplicaciones sensibles a la latencia y de alta precisión también pueden tener problemas al ejecutarse en el host. Esto se debe a que, con la virtualización habilitada, el sistema operativo host también se ejecuta sobre la capa de virtualización de Hyper-V, al igual que lo hacen los sistemas operativos invitados. Sin embargo, a diferencia de los invitados, el sistema operativo host es especial en que tiene acceso directo a todo el hardware, lo que significa que las aplicaciones con requisitos de hardware especiales se pueden seguir ejecutando sin problemas en el sistema operativo host.
## Instalación de Hyper-V en Windows

Habilitar Hyper-V para crear máquinas virtuales en Windows. Hyper-V puede habilitarse de muchas maneras, incluido mediante el panel de control de Windows, PowerShell o la herramienta de Administración y mantenimiento de imágenes de implementación (DISM). Este documento explica paso a paso cada una de las opciones.

## Comprobar los requisitos

- Windows 10 (Pro o Enterprise) o Windows 11 (Pro o Enterprise)
- Procesador de 64 bits con traducción de direcciones de segundo nivel (SLAT).
- Compatibilidad de CPU con la extensión del modo monitor de la máquina virtual (VT-c en CPU de Intel).
- Mínimo de 4 GB de memoria.
## Habilitar Hyper-V usando PowerShell

1. Abra una consola de PowerShell como administrador.
2. Ejecute el siguiente comando:

PowerShellCopiar

```
Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Hyper-V -All
```

Si no es posible encontrar el comando, asegúrate de que estás ejecutando PowerShell como administrador.

1. Cuando finalice la instalación, reinicie.
## Habilitar Hyper-V con CMD y DISM

La herramienta Administración y mantenimiento de imágenes de implementación (DISM) ayuda a configurar Windows y las imágenes de Windows. Entre sus muchas aplicaciones, DISM puede habilitar características de Windows mientras se ejecuta el sistema operativo.

Para habilitar el rol de Hyper-V mediante DISM:

1. Abra una sesión de PowerShell o CMD como administrador.
2. Escriba el siguiente comando:

PowerShellCopiar

```
DISM /Online /Enable-Feature /All /FeatureName:Microsoft-Hyper-V
```

## Habilitación del rol de Hyper-V en la configuración

1. Vaya al Panel de control.
2. Seleccione Programas y, a continuación, Programas y características.
3. Seleccione **Activar o desactivar las características de Windows**.
4. Seleccione **Hyper-V** y, a continuación, seleccione **Aceptar**.
5. Cuando finalice la instalación, se le pedirá que reinicie el equipo.

GLOSARIO:

PC: Personal Computer.
TI: Tecnologías de Información. 

Ruta por defecto de discos uros virtuales

C:\Users\Public\Documents\Hyper-V\Virtual Hard Disks

Ruta de las maquinas virtuales
C:\ProgramData\Microsoft\Windows\Hyper-V

[[202411071921]]