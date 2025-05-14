Zabbix es una solución de monitoreo distribuido de código abierto de clase empresarial.

Zabbix es un software que monitorea numerosos parámetros de una red y la salud e integridad de servidores, máquinas virtuales, aplicaciones, servicios, bases de datos, sitios web, la nube y más. Zabbix utiliza un mecanismo de notificación flexible que permite a los usuarios configurar alertas basadas en correo electrónico para prácticamente cualquier evento. Esto permite una reacción rápida ante problemas del servidor. Zabbix ofrece excelentes características de generación de informes y visualización de datos basadas en los datos almacenados. Esto hace que Zabbix sea ideal para la planificación de capacidad.

[Documentación, Manual de Zabbix](https://www.zabbix.com/la/manuals)
# Comando que puedes emplear

## Historial
Verificar acciones realizadas registradas en el servidor:
```
history
```

## Tarjeta de red

Primero instalamos el siguiente paquete `net-tools`.
```
sudo apt install net-tools
```

Ver parámetros de la tarjeta de red:
```
ifconfig
```
# Error que puede presentarse

![[Pasted image 20250509212413.png]]
El error `/usr/bin/xauth: file /home/yarold/.Xauthority does not exist` indica que el archivo oculto `.Xauthority`, que gestiona la autorización para la sesión gráfica X, no está presente o tiene problemas de permisos en tu directorio personal.

## Soluciones para el error .Xauthority en Ubuntu

### PASO 1: Crear o regenerar el archivo .Xauthority

El archivo `.Xauthority` normalmente se crea automáticamente al iniciar sesión gráfica. Si no existe, puedes intentar eliminar cualquier archivo corrupto y dejar que se regenere:

```
rm ~/.Xauthority
```

Luego cierra sesión y vuelve a iniciar sesión para que se cree de nuevo.
### PASO 2: Corregir permisos y propietario

Si el archivo existe pero tiene propietario o permisos incorrectos, puede impedir el inicio de sesión. Para corregirlo, accede a una consola con Ctrl+Alt+F1, inicia sesión y ejecuta:

```
sudo chown yarold:yarold /home/yarold/.Xauthority sudo chmod 600 /home/yarold/.Xauthorit
```

Esto asigna el archivo a tu usuario y restringe los permisos adecuadamente.
### PASO 3: Verificar permisos del directorio /tmp

En ocasiones, problemas con permisos en `/tmp` también afectan la creación de `.Xauthority`. Asegúrate que `/tmp` tiene permisos correctos:

```
sudo chmod a+wt /tmp
```

Esto da permisos de escritura y sticky bit al directorio temporal.
### PASO 4: Cambiar el gestor de sesión (opcional)

Si el problema persiste, puedes intentar reconfigurar el gestor de pantalla (por ejemplo, LightDM):

```
sudo dpkg-reconfigure lightdm
```

Luego reinicia el sistema.

Si tras estas acciones el problema continúa, puede ser útil revisar que no haya otros archivos de configuración con permisos erróneos, como `.ICEauthority`, o considerar iniciar desde un Live USB para reparar permisos en tu directorio personal.

Estas soluciones son las más comunes y efectivas para resolver errores relacionados con `.Xauthority` en Ubuntu.
