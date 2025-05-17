Herramienta de la línea de comandos de Administración remota de Windows.

Administración remota de Windows (WinRM) es la implementación de Microsoft del protocolo WS-Management, que proporciona una forma segura de comunicarse con equipos locales y remotos mediante servicios web.

Recuperar la configuración actual en formato XML.

>winrm get winrm/config -format:pretty

REM Recuperar instancia de spooler de la clase Win32_Service:
winrm get wmicimv2/Win32_Service?Name=spooler

REM Modifique una propiedad de configuración de WinRM:  
winrm set winrm/config @{MaxEnvelopeSizekb="100"}

REM Deshabilite un oyente en esta máquina:
winrm set winrm/config/Listener?Address=*+Transport=HTTPS @{Enabled="false"}

REM Crear instancia de escucha HTTP en la dirección IPv6:
winrm delete winrm/config/Listener?Address=IP:192.168.2.1+Transport=HTTP

Puedes también recuperar y modificar información de administración. Configura este equipo para que acepte solicitudes de `WS-Management` de otros equipos.