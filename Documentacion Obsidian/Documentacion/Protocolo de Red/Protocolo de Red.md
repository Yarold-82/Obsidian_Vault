**Los protocolos de red:** Como su propio nombre indica, establecen de manera detallada el proceso que deben seguir los sistemas informáticos para realizar conexiones y transferencias de información. Gracias a estos protocolos los sistemas involucrados en una comunicación son capaces de entenderse y proporcionar una interfaz homogénea para el acceso a un tipo de servicio.

Los protocolos de Internet son diversos. [[HTTP]] es el que usan los navegadores para conectarse con servidores web y recibir información de las páginas. Además, como HTTP es un protocolo tan extendido, muchos otros sistemas se apoyan en él para realizar comunicaciones, como los servicios web o diversos programas de mensajería. Pero existen otros protocolos importantes como [[IMAP]], [[POP]] y [[SNMP]] que permiten trabajar con el correo electrónico, o [FTP]] para la transferencia de archivos.
## Qué es el protocolo SSH

[[SSH]] son las siglas de Secure Shell y es un protocolo de red destinado principalmente a la conexión con máquinas a las que accedemos por línea de comandos. En otras palabras, con SSH podemos conectarnos con servidores usando la red Internet como vía para las comunicaciones. Esto es algo en lo que profundizamos en Comandos básicos para administrar [[Servidores]] Linux por SSH(https://www.arsys.es/blog/comandos-ssh-linux).

Su característica más importante es que **siempre se realiza de manera segura**. Gracias a SSH, la información que viaja por la Red no es legible por terceras personas y, para ello, todo el tránsito de la información se realiza encriptando los datos. Esto es importante para garantizar que el tráfico de datos se realice siempre de manera confidencial y que nadie sea capaz de escuchar el canal de comunicaciones para robar información o claves de acceso a los servidores.

**El puerto predeterminado para las conexiones SSH es el 22**.
## Cómo funciona SSH?

El protocolo SSH utiliza una **arquitectura cliente-servidor** para establecer conexiones seguras. Aquí hay un resumen de cómo funciona:

- **Cliente SSH**: Es la aplicación que utilizas para conectarte a un servidor remoto. Puedes utilizar diferentes clientes SSH, como OpenSSH en sistemas Linux o PuTTY en Windows.

- **Servidor SSH**: Se ejecuta en el servidor remoto al que deseas acceder. Este servidor está configurado para aceptar conexiones SSH y autenticar a los usuarios.

- **Autenticación**: Cuando intentas conectarte a un servidor remoto, el cliente SSH y el servidor SSH inician un proceso de autenticación. Esto generalmente implica el uso de un nombre de usuario y una contraseña (o una clave SSH). La clave SSH es una forma más segura de autenticación y se recomienda encarecidamente su uso.