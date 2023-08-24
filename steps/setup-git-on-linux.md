# Aplicar configuración recomendada para GIT en máquina Linux

Las siguientes instrucciones se deben ejecutar en la `terminal de linux` para aplicar configuraciones recomendadas para la máquina.

## Visualización de estados del repositorio

Crear en caso que no exista y abrir el archivo para los estilos visuales de GIT

~~~bash
nano ~/.bash_gitrc
~~~

Ajustar el contenido para que se vea como el siguiente bloque

> Al editar usando `nano` recuerde que para guardar puede presionar `Ctrl+S`, para cerrar puede presionar `Ctrl+X` o en caso de querer cerrar confirmando el guardado de cambios deberá presionar `Ctrl+X` > `Y` > `Enter`.

~~~bash
#!/bin/bash

# Show git branch name
force_color_prompt=yes
color_prompt=yes
function parse_git_branch() {
    # Variables
    declare has_colors result tmp
    has_colors=$1
    [ "${has_colors}" != "0" ] && [ "${has_colors}" != "1" ] && has_colors=0
    # Check branch
    result=$(git branch 2>/dev/null | sed -e '/^[^*]/d' -e 's/* \(.*\)/\1/')
    # Check git statuses
    [ -n "${result}" ] && [ -f .git/MERGE_HEAD ] && result="${result} | Merging"
    [ -n "${result}" ] && [ -f .git/CHERRY_PICK_HEAD ] && result="${result} | Cherry-Picking"
    # Return result
    [ -n "${result}" ] && [ ${has_colors} -eq 1 ] && result="\e[01;31m${result}\e[00m"
    [ -n "${result}" ] && result="${result}:"
    echo -e "${result}"
}
if [ "$color_prompt" = yes ]; then
    PS1='${debian_chroot:+($debian_chroot)}\[\e[01;32m\]\u@\h\[\e[00m\]:$(parse_git_branch 1)\[\e[01;34m\]\w\[\e[00m\]\n\$ '
else
    PS1='${debian_chroot:+($debian_chroot)}\u@\h:$(parse_git_branch)\w\n\$ '
fi

unset color_prompt force_color_prompt
~~~

Crear en caso que no exista y abrir el archivo de alias de bash

~~~bash
nano ~/.bash_aliases
~~~

Ajustar el contenido para que incluya el siguiente bloque

> Al editar usando `nano` recuerde que para guardar puede presionar `Ctrl+S`, para cerrar puede presionar `Ctrl+X` o en caso de querer cerrar confirmando el guardado de cambios deberá presionar `Ctrl+X` > `Y` > `Enter`.

~~~bash
# git styles
[ -f ~/.bash_gitrc ] && source ~/.bash_gitrc
~~~

> Parar visualizar los cambios en la terminal debe cerrar la instancia en que esté trabajando y abrir una nueva

## Configuración Global de Git

Crear en caso que no exista y abrir el archivo de configuración global de GIT

~~~bash
nano ~/.gitconfig
~~~

Ajustar el contenido para que incluya el siguiente bloque

> Al editar usando `nano` recuerde que para guardar puede presionar `Ctrl+S`, para cerrar puede presionar `Ctrl+X` o en caso de querer cerrar confirmando el guardado de cambios deberá presionar `Ctrl+X` > `Y` > `Enter`.

~~~ini
[core]
    editor = code --wait
[diff]
    tool = vscode
[difftool "vscode"]
    cmd = code --wait --diff $LOCAL $REMOTE
[merge]
    tool = vscode
[mergetool "vscode"]
    cmd = code --wait $MERGED
[init]
    defaultBranch = main
~~~

Guardar el nombre del usuario y el correo para la confirmación de cambios

> Reemplace `${user_name}` y `${user_email}` por el nombre y correo que quiera que queden en las confirmaciones de cambios (**commits**).

~~~bash
git config --global user.name "${user_name}"
~~~

~~~bash
git config --global user.email "${user_email}"
~~~

## Crear llave SSH en la máquina Linux

En caso que vaya a clonar repositorios privados en la máquina linux es necesario tener creada la llave SSH para la máquina.

> Para crearla en la ubicación y con el nombre predeterminados simplemente presione `Enter` sin ingresar ninguna información las veces que sea necesario hasta que se termine de ejecutar el comando.
>
> Si quiere puede cambiar el comentario `wsl-machine-ssh-key` por uno de su preferencia para identificar la llave

~~~bash
ssh-keygen -t rsa -b 4096 -C "wsl-machine-ssh-key"
~~~

## Enlaces

- [Anterior: Instalar y configurar una máquina Linux](./install-linux.md)
- [Siguiente: Instalar Docker Engine](./install-docker-engine.md)
- [Instalación y configuración de WSL en Windows](../README.md)
