Muestra las estadísticas del protocolo `NetBIOS` sobre TCP/IP (`NetBT`), las tablas de nombres NetBIOS para la computadora local, las computadoras remotas y la caché.

Este comando está disponible solo si el Protocolo de Internet (TCP/IP) está instalado como un componente en las propiedades de un adaptador de red en Conexiones de red.

Para mostrar la tabla de nombres NetBIOS de la computadora local:

> nbtstat /n

Para mostrar el contenido de la caché de nombres NetBIOS del equipo local:

> nbtstat /c

Para mostrar las estadísticas de la sesión NetBIOS por dirección IP cada cinco segundos, escriba:

> nbtstat /S 5

Para purgar la caché de nombres NetBIOS y volver a cargar las entradas _preetiquetadas en el_ archivo _Lmhosts_ local, escriba lo siguiente:

> nbtstat /r
> nbstat /rr

Este último también sirve para liberar los nombres NetBIOS con el servidor WINS y volver a registrarlos.