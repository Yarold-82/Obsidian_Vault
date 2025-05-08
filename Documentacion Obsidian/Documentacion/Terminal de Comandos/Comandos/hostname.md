Muestra el nombre del host actual. Este, probablemente es de los comandos de red más sencillos que existen.

**¿Por qué este simple comando entra en esta lista?**

Curiosamente, si no tienes una IP específica para conectarte a un host dentro de una red donde comparten un segmento de red, otra forma es haciéndolo por medio del nombre del host, que este caso, la forma de obtenerlo por consola sería ejecutando `hostname`.

> hostname
DESKTOP-V88H2KJ

Por supuesto, te comando un par de formas extras por la que se puede sacar este dato, uno de los comandos a utilizar es uno que he mostrado anteriormente, el `ipconfig`. A este, se le pasa un filtro, por ejemplo:

> ipconfig /all | find "Nombre de host"
Nombre de host. . . . . . . . . : DESKTOP-V88H2KJ