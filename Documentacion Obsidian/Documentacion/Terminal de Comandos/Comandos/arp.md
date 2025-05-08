Muestra y modifica las tablas de conversión de direcciones IP en direcciones físicas que utiliza el protocolo de resolución de direcciones ARP (_Address Resolution Protocol_).

La caché ARP contiene una o más tablas que se utilizan para almacenar direcciones IP y sus direcciones físicas Ethernet o Token Ring resueltas.

Para mostrar las tablas de caché arp para todas las interfaces, escriba:

> arp /a

![[Pasted image 20241015145703.png]]
Las direcciones IP de `inetaddr` e `ifaceaddr` se expresan en notación decimal con puntos.

La dirección física de `etheraddr` consta de seis bytes expresados en notación hexadecimal y separados por guiones (por ejemplo, 00-AA-00-4F-2A-9C).

Las entradas agregadas con el parámetro `/s` son estáticas y no se agota el tiempo de espera de la caché arp. Las entradas se eliminan si el protocolo `TCP/IP` se detiene y se inicia. Para crear entradas de caché arp estáticas permanentes, coloque los comandos arp apropiados en un archivo por lotes y use tareas programadas para ejecutar el archivo por lotes al inicio.

También puede mostrar la tabla caché de una interfaz de red específica e incluso, agregar una entrada que resuelve una dirección IP.