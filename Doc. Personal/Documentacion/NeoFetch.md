Neofetch es una herramienta de línea de comandos descontinuada, escrita en Bash, que muestra información del sistema en la terminal. De forma predeterminada, muestra el logotipo de la distribución del sistema operativo en ASCII art, junto con datos como la versión del sistema, el kernel, el entorno de escritorio, etc.

**Actualizar los repositorios**

Antes de instalar cualquier paquete, es recomendable actualizar la lista de repositorios para asegurarse de que se instalará la última versión disponible. Ejecuta en la terminal:
```
sudo apt update && apt upgrade *y*
```

**Instalar Neofetch**

Una vez actualizados los repositorios, instala Neofetch con el siguiente comando:
```
sudo apt install neofetch
```

**Ejecutar Neofetch**

Para mostrar la información de tu sistema, simplemente ejecuta:
```
neofetch
```

## Pasos para ejecución automática

1. **Editar el archivo `.bashrc`** 
Este archivo contiene comandos que se ejecutan cada vez que inicias una nueva terminal. Abre el archivo con:
```
nano ~/.bashrc
```
**Agregar el comando Neofetch**  
Desplázate al final del archivo usando las teclas de flecha y añade:
```
neofetch
```
1. Si prefieres que muestre información específica (como IP pública o privada), puedes añadir opciones adicionales, por ejemplo:  
    `neofetch --off --color_blocks off` [5](https://ugeek.github.io/blog/post/2020-06-30-informacion-de-tu-sistema-pc-servidor-con-neofetch.html).
    
2. **Guardar cambios y aplicar**  
    Presiona `Ctrl + O` para guardar y `Ctrl + X` para salir de Nano. Luego, recarga la configuración con:
```
source ~/.bashrc
```