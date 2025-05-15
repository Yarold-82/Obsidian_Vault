/etc/apache2/listen.conf

Especificar el puerto por el cual trabajara

>listen 80

En ports.conf

listen 80

IfModule ssl_module
Listen 443

IfModule mod_gnutls.c
Listen 443

/etc/apache2/sites-available/default-ssl.conf

Buscar las siguientes lineas:
`# SSLCertificateFile /etc/ssl/certs/zabbix.crt'
`# SSLCertificateKeyFile /etc/ssl/private/zabbix.key`

Y quitar los '#' para descomentar.


Lo mismo con:

/etc/apache2/sites-available/enable-ssl.conf

`# SSLCertificateFile /etc/ssl/certs/zabbix.crt`
`# SSLCertificateKeyFile /etc/ssl/private/zabbix.key
