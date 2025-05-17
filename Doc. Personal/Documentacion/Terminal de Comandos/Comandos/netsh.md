Puedo afirmar que este es uno de los comandos más potentes del sistema en cuestiones de redes.

La utilidad de secuencia de comandos de la línea de comandos `Network Shell` que le permite, ya sea de forma local o remota, mostrar o modificar la configuración de red de una computadora en ejecución.

**Restablecer la pila TCP / IP con Netsh**

Un uso común de los comandos Netsh es el restablecimiento de la pila TCP/IP que maneja el intercambio de paquetes de datos en las redes. Si aparecen problemas en la red y en Internet, esta medida puede ser de utilidad, ya que elimina, por ejemplo, los defectos o la configuración incorrecta de protocolos TCP/IP. El siguiente comando de **reparación** realiza un restablecimiento y reinstala el TCP/IPv4.

> netsh int ip reset

También puede crearse un **archivo de registro** que documente los cambios realizados:

> netsh int ip reset c:\tcpipreset.txt

Después del restablecimiento, es preciso reiniciar el ordenador.

Una de las instrucciones que personalmente uso, es la siguiente:

> netsh wlan show profile name="FullDevOps" key=clear

Investiga absolutamente todo, la línea de arriba orienta al sistema a mostrar todos aquellos perfiles de red con nombre “FullDevOps” y buscó la clave de la red donde se encuentra conectado.