Esta es una de las principales herramientas de diagnóstico que determina la ruta tomada a un destino mediante el envío de solicitudes de eco del protocolo ICMP o mensajes ICMPv6 al destino con valores de campo de tiempo de vida (TTL) que se mantienen incrementando.

Cada enrutador a lo largo de la ruta debe disminuir el TTL en un paquete IP en al menos 1 antes de reenviarlo. Efectivamente, el TTL es un contador de enlaces máximo. Cuando el TTL de un paquete llega a 0, se espera que el enrutador devuelva un mensaje de tiempo ICMP excedido a la computadora de origen.

Este comando determina la ruta enviando el primer mensaje de solicitud de eco con un TTL de 1 e incrementando el TTL en 1 en cada transmisión subsiguiente hasta que el objetivo responda o se alcance el número máximo de saltos. El número máximo de saltos es 30 de forma predeterminada y se puede especificar mediante el parámetro /h .

Para rastrear la ruta al host llamado _openwebinars.net_:

![[Pasted image 20241015154509.png]]