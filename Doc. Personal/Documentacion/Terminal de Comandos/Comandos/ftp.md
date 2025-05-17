Transfiere archivos hacia y desde una computadora que ejecuta un servicio de servidor de Protocolo de transferencia de archivos (FTP). Este comando se puede utilizar de forma interactiva o por lotes procesando archivos de texto ASCII.

> ftp ftp.microsoft.com
>Conectado a ftp.microsoft.com.
>220 cpmsftftpa03 Microsoft FTP Service (Version 5.0).
> Usuario (ftp.microsoft.com:(none)): anonymous
>331 Anonymous access allowed, send identity (e-mail name) as password.
> Contraseña:<strong>******</strong>
>230-This is FTP.MICROSOFT.COM. Please see the
>230-dirmap.txt for more information.
>230 Anonymous user logged in.

**Observaciones**

- Los parámetros de la línea de comandos de ftp distinguen entre mayúsculas y minúsculas.
    
- Este comando está disponible solo si el Protocolo de Internet (TCP / IP) está instalado como un componente en las propiedades de un adaptador de red en Conexiones de red.
    
- El comando ftp se puede utilizar de forma interactiva. Una vez iniciado, ftp crea un subentorno en el que puede utilizar comandos ftp . Puede volver a la línea de comandos escribiendo el comando ftp . Cuando se está ejecutando el subentorno ftp, se indica mediante el `ftp >`símbolo del sistema.
    
- El comando ftp admite el uso de IPv6 cuando está instalado el protocolo IPv6.

Para iniciar sesión en el servidor ftp nombrado `ftp.example.microsoft.com`y ejecutar los comandos ftp contenidos en un archivo llamado _resync.txt_ , escriba:

> ftp -s:resync.txt ftp.example.microsoft.com

Existe una variedad de comandos para acceder, subir, bajar información y por supuesto, navegar sobre el flujo del FTP.