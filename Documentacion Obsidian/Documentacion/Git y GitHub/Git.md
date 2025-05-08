## INTRODUCCIÓN A GIT

Es una herramienta de desarrollo y a su ves un Sistema de Control de Versiones de Ficheros Distribuido.

La idea, es evitar la duplicidad de data e información innecesaria y tener dentro de un proyecto en desarrollo, un control o un historial de cambios que existan, donde se puedan trazar las modificaciones.
## HISTORIA DE GIT

Básicamente, para que tengas una idea y en recordatorio, el creador del Kernel de Linux (Linus Torvald), fue el creador de GIT.

En si es como un dios mortal.
## INSTALACIÓN DE GIT

Puedes instalar GIT descargando el ejecutable e iniciándolo, directamente desde el enlace oficinal de GIT te lo dejo a continuación, [Página web oficinal de GIT](https://git-scm.com/downloads)

O puedes hacerlo usando el siguiente comando en la ventana de terminal *(Es más sencillo)*:

```
winget install --id Git.Git -e --source winget
```

*NOTA:* Estos comandos los usaras con frecuencia.

>ls / dir: Mostrar directorio.

```
ls / dir
```

>cd: Ingresar a una carpeta.

```
cd
```

>cd..: Salir de la carpeta actual y volver a la anterior.

```
cd..
```

>pwd: Mostrar ruta actual.

```
pwd
```

>clear: Limpiar terminal.

```
clear
```

>code .: Abrir visual studio code.

```
code
```

>mkdir: Crear nueva carpeta.

```
mkdir
```
## CONFIGURACIÓN DE GIT

Primeramente debes asignar el nombre y correo que estará usando GIT, es como una afiliación. 

```
git config --global user.name "name"
```

```
git config --global user.email "email"
```

Esto es para configurar la base de GIT, sin esto no podemos empezar a trabajar en GIT.

*Ubicación del archivo:* C:\Users\Yarold, en *".gitconfig"*.
*Nota:* Por si registraste algo mal.
## GIT INIT

>git init: Inicializar el repositorio local.

```
git init
```
## RAMAS EN GIT

>git branch -m *"NombreDeLaRama": "*Asignar nombre a la nueva rama*", en principio tiene de nombre *"master"*.

```
<<<<<<< HEAD
git branch -m NombreDeLaRama
=======
git branch -m "NombreDeLaRama"
>>>>>>> 8c1c46b7dae6ebee0594845f2e63b0901f6e23f8
```

>git branch -d *"NombreDeLaRama"*: Es para eliminar el nombre de la rama.

```
git branch -d "NombreDeLaRama"
```

>Otro comando para cambiar el nombre es:

```
git config --global init.defaultBranch <name>
```

En el ejercicio el nombre asignado fue *"main"*.
## GIT ADD Y COMMIT

>git add *"file"*: Anexar o añadir cada uno de los fichero en el backstage.

```
git add "file"
```

>git rm *"file"*: Elimina el el fichero del backstage.

```
git rm "file"
```

>git commit -m: Pasar los ficheros locales a remotos.

```
git commit -m
```

>git commit -m .: Pasar varios ficheros de golpe

```
git commit -m .
```
## GIT LOG Y STATUS

>git log: Al realizar el commit, muestra el hash completo, autor (nombre y correo) y date (fecha) de los ficheros actualizados.

```
git log
```

>git log --graph: Una lista de colores, separados por comas, que se puede utilizar para dibujar líneas históricas

```
git log --graph
```

>git log --graph --pretty=oneline: Muestra el historial de commits de tu repositorio de Git de forma compacta y visual:

```
git log --graph --pretty=oneline
```

>git log --graph --decorate --all --oneline: Muestra el historial de todos los commits de tu repositorio de una forma compacta, visual y muy informativa:

```
git log --graph --decorate --all --oneline
```

>git status: Es para ver el estatus de todos los ficheros.

```
git status
```
## GIT CHECKOUT Y RESET

>git checkout: Es para situarnos en un punto en concreto de un fichero, antes de establecer algún cambio.

```
git checkout
```

>git checkout "FileName": Devolver el archivo a su punto previo.

```
git checkout "FileName"
```

>git reset: Devolver el fichero a su punto de origen.

```
git reset
```
## GIT ALIAS

>git config --global alias.tree "log --graph --decorate --all --online: Establece un alias al comando para su uso.

```
git config --global alias.tree "log --graph --decorate --all --online"
```
## FICHERO .GITIGNORE

>Básicamente, luego de crear este archivo, anexa dentro de el los ficheros que estarás "ignorando" o los que no quieres tener en relevancia. Para crearlo usa la siguiente sintaxis:

```
echo ''> .gitignore
```

Y con eso ya estará creado el '.gitignore' ahora bien, para agregar los archivos o ficheros que no tomaremos en cuenta lo haremos de la siguiente manera:

>`**/.namefile`  
## echo

>echo ''>(nombre del archivo y extensión): Esto es equivalente a un *"touch"* su función es para crear un o varios ficheros. 

```
echo ''>(nombre del archivo y extensión)
```
## GIT DIFF

>git diff: Visualizar cambio sin tener que realizar un commit.

```
git diff
```

OPCIONAL:

>git config --global alias.tree "log --graph --decorate --all --oneline"

Básicamente es navegar entre los registros que se encuentre en el archivo ".git", aunque estés en un editor de código y veas que los ficheros estén depurados solo estarán fuera de la ventana pero, muy importante, ellos seguirán guardados por ende puedes recuperarlo por medio de los "HASH".
## GIT RESET HARD Y REGLOG

Es un método de cierto modo de descartar cambios, ir a una parte en concreta del archivo sin que tome nada en consideración.

Sirve para resetear cambios o situarse en un punto en concreto de la línea del tiempo del proyecto.

>git reset --hard HASH: restablece tu repositorio local a un estado exacto del commit identificado por `HASH`.

```
git reset --hard HASH
```

>git reflog: Muestra un historial local de todos los movimientos y actualizaciones recientes de las referencias en tu repositorio, especialmente de `HEAD` y las ramas.

```
git reflog
```
## GIT TAG

Un dato muy curioso del cual me acabo de enterar es que puedes añadir todos los ficheros de golpe, de la siguiente manera.

>git add .: Agrega todos los ficheros que fueran modificados.

```
git add .
```

Con `git tag` puedes asignarle una clase o id, al fichero, de manera que pueda ser mas fácil de recordar al momento que quieras realizar un llamado.

>git tag -d tag-name command: Para eliminar el tag.

```
git tag -d tag-name command
```
## GIT BRANCH Y SWITCH

Branch es para trabajar por ramas, es decir, dividir los trabajos de manera que no se mezclen, seccionarlos, es como una asignacion, basicamente divides los trabajos en cierto punto de manera que sean independientes y no tengan relacion con el proyecto principal en cierto punto.

Al finalizar cierto proyecto, en algun punto previo del mismo todos coinciden.

BRANCH directamente significa rama.

>git switch "nombre de la rama: Es empleado para navegar entre las ramas creadas.

```
git switch "nombre de la rama
```

>git branch -d login: Eliminar rama.

```
git branch -d login
```

LA MALDITA FLECHA A LA DERECHA ES QUE DEBES NAVEGAR ENTRE FICHEROS.

Recuerda eso, sufriste 1 hora por ese peo y Oded te escribió.

Aparte, tiende a perder el swicheo cuando cambias y vuelves al fichero, pendiente con ello.
## GIT EMERGE

>git merge 'nombredelfichero: El comando git merge permite tomar las líneas independientes de desarrollo creadas por git branch e integrarlas en una sola rama. Ten en cuenta que todos los comandos presentados a continuación se fusionan en la rama actual.

```
git merge 'nombredelfichero'
```
## GIT STASH 

Sirve para guardar el fichero, no realiza un 'commit' permanente, si no que realiza uno temporal que no afecta al árbol o a las ramas.

Realiza

>git stash: Realiza un guardado temporal del fichero.

```
git stash
```

>git stash list: Muestra todos los ficheros que se encuentran en espera.

```
git stash list
```

>git stash pop: Recupera todo lo que quedara en stash para trabajar a futuro.

```
git stash pop
```

>git stash drop: Elimina el stash no deseado.

```
git stash drop
```
## REINTEGRACION EN GIT

>git diff "namefile": Es para realizar comparaciones de ramas para saber si existen conflictos.

```
git diff "namefile
```

----------------
## GIT REMOTE

Administre el conjunto de repositorios ("remotos") cuyas ramas rastrea.
## GIT PUSH

>git push: El comando *"git push"* te permite subir los *commits* desde tu rama *(branch)* local en tu repositorio git local al repositorio remoto.

```
git push
```
## GIT FETCH Y PULL

>git fetch: Se descarga el historial sin los cambios.

```
git fetch
```

>git pull: Se descarga el historial con los cambios.

```
git pull
```
## GIT CLONE

>git clone: Generalmente es seguro clonar repositorios remotos con contenido no confiable e inspeccionarlos.

```
git clone "url"
```
## GIT LS & RM

Estos pasos son para borrar ciertos ficheros del backstage de manera que no se puedan hacer push.

>git ls-files: Este comando fusiona la lista de archivos en el índice con la lista real del directorio de trabajo y muestra diferentes combinaciones de los dos.

```
git ls-files
```

git rm --cached -r "ruta a verificar": Elimine los archivos que coincidan con la especificación de ruta del índice o del árbol de trabajo y del índice. `git rm` no eliminará un archivo solo de su directorio de trabajo.

Cuando `--cached` si se proporciona, el contenido por etapas debe coincidir con la punta de la rama o con el archivo en el disco, lo que permite eliminar el archivo solo del índice.

```
git rm --cached -r "ruta a verificar"
```

Luego aplicamos un git commit.

```
git commit -m "Registrar el borrado de cache"
```

## GIT SHOW

>git show: Muestra uno o más objetos (blobs, árboles, etiquetas y confirmaciones.

```
git show
```