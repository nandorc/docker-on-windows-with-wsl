# Instalar WSL2

WSL permitirá la ejecución de una máquina Linux sobre su entorno Windows. Para ello deberá ejecutar algunos comandos.

## Habilitar características en la máquina Windows

Valide los [requerimientos para ejecutar WSL2](https://learn.microsoft.com/en-us/windows/wsl/install-manual#step-2---check-requirements-for-running-wsl-2) y ejecute en `powershell` con permisos de Administrador los siguientes comandos.

~~~powershell
dism.exe /online /enable-feature /featurename:Microsoft-Windows-Subsystem-Linux /all /norestart
~~~

~~~powershell
dism.exe /online /enable-feature /featurename:VirtualMachinePlatform /all /norestart
~~~

Al finalizar **REINICIE** su máquina Windows.

## Descargar e instalar el paquete de actualización del Kernel de Linux

Descargue e instale el [paquete de actualización del kernel de linux](https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi) y al finalizar **REINICIE** su máquina Windows

## Configurar la versión a usar de WSL

Ejecute el siguiente comando en `powershell`.

~~~powershell
wsl --set-default-version 2
~~~

## Enlaces

- [Anterior: Instalar Extensión de VSCode recomendada](./install-vscode-extension.md)
- [Siguiente: Instalar y configurar una máquina Linux](./install-linux.md)
- [Instalación y configuración de WSL en Windows](../README.md)
