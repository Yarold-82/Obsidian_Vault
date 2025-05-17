Muestra las conexiones TCP activas, los puertos en los que la computadora está escuchando, las estadísticas de Ethernet, la tabla de enrutamiento de IP, las estadísticas de IPv4 (para los protocolos `IP`, `ICMP`, `TCP` y `UDP`) y las estadísticas de IPv6 (para `IPv6`, `ICMPv6`, `TCP` sobre IPv6 y `UDP` sobre protocolos IPv6).

Para mostrar tanto las estadísticas de Ethernet como las estadísticas de todos los protocolos:

>netstat -e -s

Para mostrar las estadísticas solo para los protocolos TCP y UDP:

>netstat -s -p tcp udp

Para mostrar las conexiones TCP activas y los ID de proceso cada 5 segundos:

>netstat -o 5

Para mostrar las conexiones TCP activas y los ID de proceso en forma numérica:

>netstat -n -o

La diferencia con el anterior `nbtstat` es que este no usa NetBIOS.

>netstat -ano

Buscar puerto en el listado de puertos.

>netstat -ano | findstr "8080"

Verificar si dicho host escucha un puerto

>ss -l4 | grep 8080

En Linux, es lo mismo que netstat -ano
 
>sudo netstat -tulpn