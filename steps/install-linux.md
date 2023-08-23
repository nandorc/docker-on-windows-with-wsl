# Instalar y configurar una máquina Linux

Teniendo WSL2 en su máquina lo que procedería sería la instalación del Ubuntu.

## Instalar Ubuntu

Ejecute en `powershell` el siguiente comando.

> Procure no realizar ninguna acción mientras el comando se ejecuta, al finalizar la instalación se le solicitará indicar un nombre de usuario UNIX y una contraseña para la distro de Ubuntu instalada.
>
> Al momento del registro de estos pasos la version que se instala al finalizar el proceso es `Ubuntu 22.04.2 LTS`

~~~bash
wsl --install -d Ubuntu
~~~

> En caso de tener inconvenientes en la instalación, pruebe ejecutar el comando `wsl --list --online` y verifique que la opción `Ubuntu` se encuentre entre las allí listadas.
>
> Si lo ve necesario, instale una versión especifica de Ubuntu de las que verá listadas al ejecutar el comando.

## Configurar Ubuntu

Ejecute los siguientes comandos en la `terminal de ubuntu` para realizar la configuración inicial recomendada

~~~bash
touch ~/.hushlogin
~~~

~~~bash
sudo passwd -d $USER
~~~

~~~bash
sudo apt-get update
~~~

~~~bash
sudo apt-get upgrade -y
~~~

## Enlaces

**Anterior:** [Instalar WSL2](./install-wsl-2.md)

**Siguiente:** [Instalar Docker Engine](./install-docker-engine.md)

**Inicio:** [Instalación y Habilitación de Docker Engine en Windows usando WSL](../README.md)
