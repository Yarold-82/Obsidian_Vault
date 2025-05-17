Wget es una utilidad gratuita, disponible para Mac, `Windows` y Linux (incluida), que puede ayudarlo a lograr todo esto y más. Lo que lo diferencia de la mayoría de los administradores de descargas es que wgetpuede seguir los enlaces HTML en una página web y descargar los archivos de forma recursiva.

Muestro esta herramienta porque en Windows, existe de forma nativa el comando `bitsadmin`, pero que ya se encuentra en desuso.

Descargue un solo archivo de Internet

> wget http://example.com/file.iso

Descargue un archivo, pero guárdelo localmente con un nombre diferente

> wget ‐‐output-document=filename.html example.com

Descarga un archivo y guárdalo en una carpeta específica

> wget ‐‐directory-prefix=folder/subfolder example.com

Reanudar una descarga interrumpida previamente iniciada por el propio wget

> wget ‐‐continue example.com/big.file.iso

Descargue un archivo, pero solo si la versión en el servidor es más reciente que su copia local

> wget ‐‐continue ‐‐timestamping wordpress.org/latest.zip

El comando wget ejercerá una presión adicional sobre el servidor del sitio porque atravesará continuamente los enlaces y descargará archivos.