## INTRODUCCIÓN A GITHUB

Primeramente debemos dejar en claro que GIT Y GITHUB no son lo mismo.

Git: Es un sistema de control de versiones, nos permite trabajar con el código de manera segura de forma local.

GitHub: Es una plataforma que por debajo utiliza Git, pero la diferencia que tiene es que trabaja en la nube de manera remota, en donde pueden interactuar varias personas.

[ENLACE DIRECTO](https://github.com)
[DESCARGA ESTO](https://training.github.com/donwloads/es_ES/github-git-cheat-sheet.pdf)
[DOCUMENTACIÓN DE GITHUB](https://docs.github.com/es)
## AUTENTICACION SSH

Antes de comenzar, esto fue realizado dos veces en maquinas diferentes para probar el funcionamiento, dando como resultado uno positivo, tendrás que trabajar con `PowerShell` en Administrador o para no tener muchas complicaciones usa el `Bash Git` (Recomendado), tiene mucha relación con linux y de igual forma usaras por un momento el `nano`
## Generar una nueva llave SSH

Puedes generar una nueva clave SSH en el equipo local. Después de generar la clave, puede agregar la clave pública a la cuenta en GitHub.com para habilitar la autenticación para las operaciones de Git a través de SSH.

Estar dentro de la carpeta .ssh

```shell
ssh-keygen -t ed25519 -C "your_email@example.com"
```

Luego de establecer el correo, te solicitara el nombre de la llave "ssh", el estándar es: id_rsa

> `Enter file in which to save the key (C:\Users\Yarold/.ssh/id_ed25519): ``

Luego te pedirá la clave y una confirmación:

> `Enter passphrase (empty for no passphrase):`
> `Enter same passphrase again:`
## Inicio automático `ssh-agent` en Git para Windows

Puede ejecutar `ssh-agent` automáticamente al abrir bash o el shell de Git. Copie las líneas siguientes y péguelas en su archivo `~/.profile` o `~/.bashrc` en el shell de Git:

```
env=~/.ssh/agent.env

agent_load_env () { test -f "$env" && . "$env" >| /dev/null ; }

agent_start () {
    (umask 077; ssh-agent >| "$env")
    . "$env" >| /dev/null ; }

agent_load_env

# agent_run_state: 0=agent running w/ key; 1=agent w/o key; 2=agent not running
agent_run_state=$(ssh-add -l >| /dev/null 2>&1; echo $?)

if [ ! "$SSH_AUTH_SOCK" ] || [ $agent_run_state = 2 ]; then
    agent_start
    ssh-add
elif [ "$SSH_AUTH_SOCK" ] && [ $agent_run_state = 1 ]; then
    ssh-add
fi

unset env
```

Aquí es donde usarás `nano` y `Git Bash`, luego de haber hecho lo indicado, cierra el shell de git, ábrelo nuevamente y te debería pedir una clave para iniciar el svr ssh.
## Agregar tu clave SSH al ssh-agent

En una ventana de terminal sin permisos elevados, agregue la clave privada SSH al agente ssh. Si has creado tu clave con otro nombre o si vas a agregar una clave existente que tiene otro nombre, reemplaza _id_ed25519_ en el comando por el nombre de tu archivo de clave privada.

> `ssh-add c:/Users/YOU/.ssh/id_ed25519`

`Ejecutar en Git Bash`
## Configurar llave SSH en GitHub

Antes de probar la conexion SSH, tienes que configurar la llave ".pub ssh en github", añádela, asigna el nombre de la maquina y listo.
## Probar tu conexión SSH

Deberá autenticar esta acción utilizando su contraseña, que es la contraseña de clave SSH que ya creó:

> `ssh -T git@github.com`

```shell
> The authenticity of host 'github.com (IP ADDRESS)' can't be established.
> ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
> Are you sure you want to continue connecting (yes/no)?
```

Compruebe que la huella digital del mensaje que ve coincide con [la huella digital de clave pública de GitHub](https://docs.github.com/es/authentication/keeping-your-account-and-data-secure/githubs-ssh-key-fingerprints). En caso afirmativo, escriba `yes`: