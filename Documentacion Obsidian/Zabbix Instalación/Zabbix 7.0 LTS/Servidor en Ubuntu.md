[Documentacion Debian/Ubuntu](https://www.zabbix.com/documentation/current/es/manual/installation/upgrade/packages/debian_ubuntu)

## Paso 1: Cambiar a sudo, de la Siguiente Manera:

```
user@machine:~$ sudo -i
```

Al darle "Enter" te pedirá la clave del usuario "sudo" (Si es que tiene clave) `[sudo] password for user:` ingresa la misma y dale "Enter", luego de estarás en como sudo y lo comprobaras de la siguiente manera:

```
root@machine:
```

Nota: Con este comando se puede ingresar como sudo `sudo -s`.

Luego de eso, actualizar el servidor, para eso utiliza el siguiente comando.
```
root@machine:~$ apt update && upgrade -y
```
## Paso 2: Actualizar el Repositorio de Zabbix.

 ```
wget https://repo.zabbix.com/zabbix/7.0/ubuntu/pool/main/z/zabbix-release/zabbix-release_latest+ubuntu24.04_all.deb
dpkg -i zabbix-release_latest+ubuntu24.04_all.deb
apt update
```
## Paso 3: Instala Zabbix Server, el FrontEnd, y el agent.

```
apt install zabbix-server-mysql zabbix-frontend-php zabbix-apache-conf zabbix-sql-scripts zabbix-agent
```
## Paso 4: Verificar los Servicios del Zabbix y Activar los Correspondientes.

Para verificar el estatus del Zabbix:
```
systemctl status zabbix-server
```

Para iniciar el servidor, luego de eso verifica el estatus del mismo:
```
systemctl start zabbix-server
```

Verificar el estatus del agent:
```
systemctl status zabbix-agent
```

Habilitar servidor:
```
systemctl enable zabbix-server
```

Habilitar el agente:
```
systemctl enable zabbix-agent
```

Reiniciar el Agente:
```
systemctl restart zabbix-agent.service
```

```
systemctl restart zabbix-server.service
```

```
systemctl restart apache2.service
```
## Paso 5: Crea la Base de Datos

Instalar mysql server
```
apt install mysql-server
```

Luego de eso debes ingresar a mysql

```
mysql
```

Y ejecuta los siguientes comandos

```
create database zabbix character set utf8mb4 collate utf8mb4_bin;
```

```
create user zabbix@localhost identified by 'password'; (La clave es de prueba, debes poner una real)
```

```
grant all privileges on zabbix.* to zabbix@localhost;
```

```
set global log_bin_trust_function_creators = 1;
```

```
quit;
```

## Paso 6: Importar Esquema y Datos Iniciales

En el host del servidor Zabbix, importe el esquema y los datos iniciales. Se le pedirá que ingrese su contraseña recién creada.

```
zcat /usr/share/zabbix-sql-scripts/mysql/server.sql.gz | mysql --default-character-set=utf8mb4 -uzabbix -p zabbix
```
## Paso 7: Configure la base de datos para el servidor Zabbix:

Edit file `/etc/zabbix/zabbix_server.conf`

> `DBPassword=password`