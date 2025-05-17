Obtener datos de la configuración de red TCP/IP nunca fue tan sencillo como utilizar el comando `ipconfig`, que precisamente obtener esta información y actualiza la configuración del protocolo de configuración dinámica de host (DHCP) y del sistema de nombres de dominio (DNS).

El modo de uso es tan sencillo como escribir: `ipconfig`.  
Te muestro cómo filtra la información por el protocolo `IPv4`.

> ipconfig | find "IPv4"

De este modo, en la salida generará las direcciones IPv4 de todos los adaptadores de red instalados en el equipo.

> ipconfig | find "IPv4"

Dirección IPv4. . . . . . . . . . . . . . : 192.168.56.1
Dirección IPv4. . . . . . . . . . . . . . : 192.168.2.1
Dirección IPv4. . . . . . . . . . . . . . : 192.168.0.2

Para mostrar la configuración de TCP/IP completa para todos los adaptadores, escriba `ipconfig /all`, sin embargo, para ser un poco más precisos, extraeremos la `Descripción` de cada adaptador de red. En caso de que tengas el ordenador en inglés, escribes `Description`.

